---
title: python script streaming (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'streaming'

Functions in program: 
* `def make_app():`
* `def data_source(x=10):`

Modules used in program: 
* `import tornado.ioloop`
* `import tornado.web`
* `import tornado.websocket`
* `import logging`
* `import random`
* `import sys`
* `import random`
* `import os.path`
* `import os`

## python streaming

Python mysql example: streaming

```python
import os
import os.path
import random
import sys
import random
import logging
import tornado.websocket
import tornado.web
import tornado.ioloop
from datetime import datetime

sys.path.insert(1, os.path.join(os.path.dirname(__file__), '..'))
from perspective import Table, PerspectiveManager, PerspectiveTornadoHandler


class MainHandler(tornado.web.RequestHandler):

    def set_default_headers(self):
        self.set_header("Access-Control-Allow-Origin", "*")
        self.set_header("Access-Control-Allow-Headers", "x-requested-with")
        self.set_header('Access-Control-Allow-Methods', 'POST, GET, OPTIONS')

    def get(self):
        self.render("streaming.html")


def data_source(x=10):
    rows = []
    modifier = random.random() * random.randint(1, 50)
    for i in range(x):
        rows.append({
            "id": i,
            "name": SECURITIES[random.randint(0, len(SECURITIES) - 1)],
            "client": CLIENTS[random.randint(0, len(CLIENTS) - 1)],
            "open": (random.random() * 75 + random.randint(0, 9)) * modifier,
            "high": (random.random() * 105 + random.randint(1, 3)) * modifier,
            "low": (random.random() * 85 + random.randint(1, 3)) * modifier,
            "close": (random.random() * 90 + random.randint(1, 3)) * modifier,
            "lastUpdate": datetime.now()
        })
    return rows


'''Set up our data for this example.'''
SECURITIES = ["AAPL.N", "AMZN.N", "QQQ.N", "NVDA.N", "TSLA.N", "FB.N", "MSFT.N", "TLT.N", "XIV.N", "YY.N", "CSCO.N", "GOOGL.N", "PCLN.N"]
CLIENTS = ["Homer", "Marge", "Bart", "Lisa", "Maggie", "Moe", "Lenny", "Carl", "Krusty"]


def make_app():
    # Create an instance of `PerspectiveManager` and a table.
    MANAGER = PerspectiveManager()
    TABLE = Table(data_source(1000), index="id")

    # Track the table with the name "data_source_one", which will be used in
    # the front-end to access the Table.
    MANAGER.host_table("data_source_one", TABLE)

    # update with new data every 50ms
    def updater():
        ids = TABLE.view(columns=["id"]).to_dict().get("id", None)
        if ids is not None:
            to_remove = random.sample(ids, 5)
            TABLE.remove(to_remove)

    callback = tornado.ioloop.PeriodicCallback(callback=updater, callback_time=500)
    callback.start()

    return tornado.web.Application([
        (r"/", MainHandler),
        # create a websocket endpoint that the client Javascript can access
        (r"/websocket", PerspectiveTornadoHandler, {"manager": MANAGER, "check_origin": True})
    ])


if __name__ == "__main__":
    app = make_app()
    app.listen(8888)
    logging.critical("Listening on http://localhost:8888")
    loop = tornado.ioloop.IOLoop.current()
    loop.start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
