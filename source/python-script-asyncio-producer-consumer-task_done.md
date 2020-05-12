---
title: python script asyncio-producer-consumer-task done (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'asyncio-producer-consumer-task done'

Functions in program: 
* `def run(n):`
* `def consume(queue):`
* `def produce(queue, n):`

Modules used in program: 
* `import random`
* `import asyncio`

## python asyncio-producer-consumer-task done

Python example: asyncio-producer-consumer-task done

```python
# Original source from http://asyncio.readthedocs.io/en/latest/producer_consumer.html
# Rewritten for Python >=3.4

import asyncio
import random


@asyncio.coroutine
def produce(queue, n):
    for x in range(n):
        # produce an item
        print('producing {}/{}'.format(x, n))
        # simulate i/o operation using sleep
        yield from asyncio.sleep(random.random())
        item = str(x)
        # put the item in the queue
        yield from queue.put(item)


@asyncio.coroutine
def consume(queue):
    while True:
        # wait for an item from the producer
        item = yield from queue.get()

        # process the item
        print('consuming {}...'.format(item))
        # simulate i/o operation using sleep
        yield from asyncio.sleep(random.random())

        # Notify the queue that the item has been processed
        queue.task_done()


@asyncio.coroutine
def run(n):
    queue = asyncio.Queue()
    # schedule the consumer
    consumer = asyncio.ensure_future(consume(queue))
    # run the producer and wait for completion
    yield from produce(queue, n)
    # wait until the consumer has processed all items
    yield from queue.join()
    # the consumer is still awaiting for an item, cancel it
    consumer.cancel()


if __name__ == "__main__":
    loop = asyncio.get_event_loop()
    loop.run_until_complete(run(10))
    loop.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
