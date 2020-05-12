---
title: python script sample2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sample2'

Functions in program: 
* `def _http():`
* `def fetch(uri):`
* `def main():`

Modules used in program: 
* `import random`
* `import asyncio`

## python sample2

Python example: sample2

```python
import asyncio
import random


URIS = ("http://example.org/foo", "http://example.org/bar",
        "http://example.org/baz")


def main():
    for uri in URIS:
        task = asyncio.Task(fetch(uri))
        print("---- registered %s" % task)


@asyncio.coroutine
def fetch(uri):
    print("retrieving %s..." % uri)
    response = yield from _http()
    print("downloaded %s kB" % response)
    return response


@asyncio.coroutine
def _http():
    yield from asyncio.sleep(1.0)
    return random.randint(0, 9)


main()
loop = asyncio.get_event_loop()
try:
    loop.run_forever()
finally:
    loop.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
