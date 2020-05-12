---
title: python script reactor (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reactor'

Functions in program: 
* `def test():`

Modules used in program: 
* `import sys`
* `import logging`
* `import json`
* `import http.client`

## python reactor

Python mysql example: reactor

```python
#!/usr/bin/env python3

import http.client
import json
import logging
import sys
from functools import lru_cache

logging.basicConfig(stream=sys.stdout, level=logging.WARNING)

class Reactor(object):
    conn = http.client.HTTPConnection("localhost", 8081);
    
    def __init__(self, x, z, height, layout):
        if len(layout) != x * z:
            raise ValueError("Layout must be {} for a {} * {} reactor".format(x * z, x, z))

        self.x = x + 2 # I use interior dimensions like the website - the API does not
        self.z = z + 2
        self.height = height + 2
        self.layout = layout
        self.controlRodInsertion = 0
        self.activelyCooled = False

    def to_definition_json(self):
        data_json = json.dumps(
            {
             "xSize": self.x,
             "zSize": self.z,
             "height": self.height,
             "layout": self.layout,
             "controlRodInsertion": self.controlRodInsertion,
             "activelyCooled": self.activelyCooled
            },
            separators=(',', ':')
        )
        logging.debug("Reactor Definition : %s" % data_json)
        return data_json

    @lru_cache(maxsize=10)
    def test_reactor(self):
        Reactor.conn.request("GET", "/api/simulate?definition={}".format(self.to_definition_json()))
        res = Reactor.conn.getresponse()
        res_text = res.read().decode("utf-8")

        logging.debug("Response Text: %s" % res_text)
        
        if res_text.startswith("UNEXPECTED"):
            logging.info("Server returned error: %s" % res_text)
            return False
        res_json = json.loads(res_text)
        self.response_cache = res_json
        logging.debug("Decoded JSON: %s" % res_json)
        return res_json

    @property
    def power(self):
        data = self.test_reactor()
        if data is False:
            return False
        return data["output"]

    @property
    def efficiency(self):
        data = self.test_reactor()
        if data is False:
            return False
        return data["output"] / data["fuelConsumption"]

    def pretty_result(self):
        if self.power is False:
            print("Reactor failed! (did it have any fuel rods?)")
        else:
            print("Size: {}*{}*{} Layout: {} Power: {} RF/mB: {}".format(
                self.x, self.z, self.height, self.layout, self.power, self.efficiency))

def test():
    r = Reactor(3, 3, 1, "LXLXXXLXL")
    r.pretty_result()

if __name__ == "__main__":
    test()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
