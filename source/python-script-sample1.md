---
title: python script sample1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sample1'

Functions in program: 
* `def _http():`
* `def fetch(uri):`
* `def main():`

Modules used in program: 
* `import random`
* `import asyncio`

## python sample1

Python mysql example: sample1

```python
import asyncio
import random


URIS = ("http://example.org/foo", "http://example.org/bar",
        "http://example.org/baz")


@asyncio.coroutine
def main():
    for uri in URIS:
        res = yield from fetch(uri)
        print("---- %s (%s)" % (res, uri))


@asyncio.coroutine
def fetch(uri):
    print("GET %s" % uri)
    response = yield from _http()
    print("%s kB" % response)
    return response


@asyncio.coroutine
def _http():
    yield from asyncio.sleep(1.0)
    return random.randint(0, 9)


loop = asyncio.get_event_loop()
loop.run_until_complete(main())
loop.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
