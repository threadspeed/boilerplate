---
title: python script sample3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sample3'

Functions in program: 
* `def _http():`
* `def fetch(uri):`
* `def main(loop):`

Modules used in program: 
* `import random`
* `import asyncio`

## python sample3

Python mysql example: sample3

```python
import asyncio
import random


URIS = ("http://example.org/foo", "http://example.org/bar",
        "http://example.org/baz")


def main(loop):
    req_count = 0

    def shutdown():
        if req_count == len(URIS):
            loop.stop()

    for uri in URIS:
        task = asyncio.Task(fetch(uri))
        task.add_done_callback(lambda task: shutdown())
        req_count += 1
        print("---- registered #%s %s" % (req_count, task))


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


loop = asyncio.get_event_loop()
main(loop)
try:
    loop.run_forever()
finally:
    loop.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
