---
title: python script sample0 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sample0'

Functions in program: 
* `def _http():`
* `def fetch(uri):`
* `def main():`

Modules used in program: 
* `import random`
* `import time`

## python sample0

Python example: sample0

```python
import time
import random


URIS = ("http://example.org/foo", "http://example.org/bar",
        "http://example.org/baz")


def main():
    for uri in URIS:
        res = fetch(uri)
        print("---- %s (%s)" % (res, uri))


def fetch(uri):
    print("GET %s" % uri)
    response = _http()
    print("%s kB" % response)
    return response


def _http():
    time.sleep(1.0)
    return random.randint(0, 9)


main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
