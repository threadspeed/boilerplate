---
title: python script load tester (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'load tester'


Modules used in program: 
* `import pandas as pd`
* `import time, datetime, string, csv`
* `import aiohttp`
* `import aiofiles`
* `import urllib.parse`
* `import urllib.error`
* `import sys`
* `import re`
* `import logging`
* `import asyncio`

## python load tester

Python example: load tester

```python
"""
Asynchronously send requests to local API.
Simply configure path and parameters in set-up below
and run `python load_tester.py` in the terminal.
"""

import asyncio
import logging
import re
import sys
from typing import IO
import urllib.error
import urllib.parse

import aiofiles
import aiohttp
from aiohttp import ClientSession

import time, datetime, string, csv
import pandas as pd

logging.basicConfig(
    format="%(asctime)s %(levelname)s:%(name)s: %(message)s",
    level=logging.DEBUG,
    datefmt="%H:%M:%S",
    stream=sys.stderr,
)
logger = logging.getLogger("areq")
logging.getLogger("chardet.charsetprober").disabled = True


class LoadTester:
    '''
    This load tester tests how much your API (specified by host)
    can handle, given the parameters and data.

    The code is based on:
    https://realpython.com/async-io-python/#a-full-program-asynchronous-requests
    '''

    def __init__(self, host, params, outpath, data):
        self.host = host        # e.g. http://127.0.0.1:8000/
        self.params = params    # e.g. "api/incredible/?model_input="
        self.outpath = outpath  # e.g. results.csv
        self.data = data        # e.g. ['abc', 'cde', ...]
        self.uri = self.host + self.params
        self.time_taken = None


    def start_testing(self):
        """ Set up and start the Celery Loop. """
        global_start = time.time()
        loop = asyncio.get_event_loop()
        futures = self.schedule_requests(file=self.outpath, uri=self.uri, data=self.data)
        loop.run_until_complete(futures)
        self.time_taken = time.time() - global_start


    async def api_request(self, url, session, **kwargs):
        """
        GET request wrapper to make GET API call
        kwargs are passed to `session.request()`.

        Return list of infos
        resp = [start, url, status_code, response_time, content]
        """
        start = time.time()
        response = await session.request(method="GET", url=url, **kwargs)
        response.raise_for_status()
        logger.info("Got response [%s] for URL: %s", response.status, url)

        # current_time = datetime.datetime.fromtimestamp(start).strftime('%Y-%m-%d %H:%M:%S.%f')
        current_time = start
        status_code = response.status
        response_time = time.time() - start
        content = await response.text()
        resp = [current_time, url, status_code, response_time, content]
        return resp


    async def handle_request(self, url, session, **kwargs):
        """Make HTTP request and handle exceptions."""
        try:
            resp = await self.api_request(url=url, session=session, **kwargs)
        except (
            aiohttp.ClientError,
            aiohttp.http_exceptions.HttpProcessingError,
        ) as e:
            logger.error(
                "aiohttp exception for %s [%s]: %s",
                url,
                getattr(e, "status", None),
                getattr(e, "message", None),
            )
            start = time.time()
            # current_time = datetime.datetime.fromtimestamp(start).strftime('%Y-%m-%d %H:%M:%S.%f')
            current_time = start
            status_code = getattr(e, "status", None)
            response_time = time.time() - start
            content = "aiohttp exception"
            resp = [current_time, url, status_code, response_time, content]
            return resp
        except Exception as e:
            logger.exception(
                "Non-aiohttp exception occured:  %s", getattr(e, "__dict__", {})
            )
            start = time.time()
            # current_time = datetime.datetime.fromtimestamp(start).strftime('%Y-%m-%d %H:%M:%S.%f')
            current_time = start
            status_code = '000'
            response_time = time.time() - start
            content = "non-aiohttp exception"
            resp = [current_time, url, status_code, response_time, content]
            return resp
        else:
            return resp


    async def write_result(self, file, url, **kwargs):
        """Write the request response to `file`."""
        response = await self.handle_request(url=url, **kwargs)
        if not response:
            return None
        with open(file, "a") as outfile:
            time, request, status_code, response_time, content = response
            writer = csv.writer(outfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
            writer.writerow([time, request, status_code, response_time, content])
            logger.info("Wrote results for source URL: %s", url)

    async def schedule_requests(self, file, uri, data, **kwargs):
        """
        Concurrently make request to URI with parameters words and
        write output to `file`.
        """
        async with ClientSession() as session:
            tasks = []
            for d in data:
                url = uri + d
                tasks.append(
                    self.write_result(file=file, url=url, session=session, **kwargs)
                )
            await asyncio.gather(*tasks)

    def analyze_performance(self):
        results = pd.read_csv(self.outpath)

        # requests per second
        seconds = self.time_taken
        requests = results.shape[0]
        print(seconds, requests)
        rps = requests/seconds

        # response counts
        response_counts = results['status_code'].value_counts()

        print('REQUESTS PER SECOND', rps)
        print('STATUS CODE RESPONSE COUNTS \n', response_counts)
        return rps, response_counts

if __name__ == "__main__":
    import pathlib
    import sys
    import random
    import string

    # Incredible API
    host = "http://127.0.0.1:8000/"
    params = "api/incredible/?model_input="  # simplified parameter input
    N = 1000 # datapoints
    data = ["".join(random.choices(string.ascii_lowercase[:5], k=2)) for i in range(N)]
    here = pathlib.Path(__file__).parent
    outpath = here.joinpath("incredible_results.csv")
    with open(outpath, "w") as outfile:
        writer = csv.writer(outfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
        writer.writerow(['time', 'request', 'status_code', 'response_time', 'content'])

    LT = LoadTester(host=host, params=params, outpath=outpath, data=data)
    LT.start_testing()
    incredible_results = LT.analyze_performance()


    # Database APIs
    host = "http://127.0.0.1:8000/"
    params = "api/company/?starts_with="  # simplified parameter input
    N = 1000 # datapoints
    data = random.choices(string.ascii_uppercase, k=N)
    here = pathlib.Path(__file__).parent
    outpath = here.joinpath("db_results.csv")
    with open(outpath, "w") as outfile:
        writer = csv.writer(outfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
        writer.writerow(['time', 'request', 'status_code', 'response_time', 'content'])

    LT = LoadTester(host=host, params=params, outpath=outpath, data=data)
    LT.start_testing()
    db_results = LT.analyze_performance()

    print('INCREDIBLE RESULTS\n')
    print(incredible_results)
    print('DB RESULTS\n')
    print(db_results)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
