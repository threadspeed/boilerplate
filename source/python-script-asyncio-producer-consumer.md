---
title: python script asyncio-producer-consumer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'asyncio-producer-consumer'

Functions in program: 
* `def consume(queue):`
* `def produce(queue, n):`

Modules used in program: 
* `import random`
* `import asyncio`

## python asyncio-producer-consumer

Python example: asyncio-producer-consumer

```python
# Original source from http://asyncio.readthedocs.io/en/latest/producer_consumer.html
# Rewritten for Python >=3.4

import asyncio
import random


@asyncio.coroutine
def produce(queue, n):
    for x in range(1, n + 1):
        # produce an item
        print('producing {}/{}'.format(x, n))
        # simulate i/o operation using sleep
        yield from asyncio.sleep(random.random())
        item = str(x)
        # put the item in the queue
        yield from queue.put(item)

    # indicate the producer is done
    yield from queue.put(None)


@asyncio.coroutine
def consume(queue):
    while True:
        # wait for an item from the producer
        item = yield from queue.get()
        if item is None:
            # the producer emits None to indicate that it is done
            break

        # process the item
        print('consuming item {}...'.format(item))
        # simulate i/o operation using sleep
        yield from asyncio.sleep(random.random())


if __name__ == "__main__":
    loop = asyncio.get_event_loop()
    queue = asyncio.Queue(loop=loop)
    producer_coro = produce(queue, 10)
    consumer_coro = consume(queue)
    loop.run_until_complete(asyncio.gather(producer_coro, consumer_coro))
    loop.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
