---
title: python script postall (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'postall'

Functions in program: 
* `def get_queue(limit=None):`
* `def get_files(limit=None):`
* `def postfile(name, connection):`
* `def pollQueue():`

Modules used in program: 
* `import os`
* `import sys`
* `import random`
* `import hashlib`
* `import http.client`

## python postall

Python example: postall

```python
#!/bin/env python3
# vim: expandtab shiftwidth=4 softtabstop=4 tabstop=17 filetype=python :
"""
Upload a set of .csr files to a caramel endpoint. Used for some minor
benchmarking and to populate things"""


import http.client
import hashlib
import random
import sys
import os


from threading import Thread, current_thread
from queue import Queue

ENDPOINT = "devnull-as-a-service.com"
CSRDIR = '/tmp/csr'
concurrent = 60  # 60 threads + 60 https connections


def pollQueue():
    # Set up one connection per thread, and re-use that
    conn = http.client.HTTPSConnection(ENDPOINT, 443)
    count = 0
    while True:
        fname = TheQueue.get()
        postfile(fname, conn)
        TheQueue.task_done()  # Mark a task as consumed, for queue.wait()
        count += 1
        if count % 100 == 0:
            print("{}: {}  ({} remaining)".format(current_thread(),
                                                  count, TheQueue.qsize()))
    conn.close()

def postfile(name, connection):
    """The filename is the sha256sum in hex of the CSR.
    Calculate it, and post the data"""
    with open(name, 'rb') as f:
        data = f.read()
    sha = hashlib.sha256(data).hexdigest()
    connection.request("POST", '/dev/null', body=data)
    # If we don't read the response data, we cannot reuse the connection
    result = connection.getresponse()
    result.read()
    return result.status


def get_files(limit=None):
    """Returns an iterator of filenames, shuffled."""

    print("Listing files")
    files = os.listdir(CSRDIR)
    total = len(files)
    limit = limit if limit else total

    print("Shuffling: {} files".format(total))
    random.shuffle(files)
    for f in files[:limit]:
        yield "{}/{}".format(CSRDIR, f)


def get_queue(limit=None):
    print("Queueing {} items".format(limit))
    q = Queue(limit if limit else 0)
    for fname in get_files(limit):
        q.put(fname)
    return q

if __name__ == "__main__":
    TheQueue = get_queue()

    print("Setting up {} threads".format(concurrent))
    for i in range(concurrent):
        t = Thread(target=pollQueue)
        t.daemon = True
        t.start()

    try:
        TheQueue.join()
    except KeyboardInterrupt:
        sys.exit(1)

    print("All jobs done")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
