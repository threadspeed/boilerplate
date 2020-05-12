---
title: python script example with semaphore (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'example with semaphore'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`
* `import asyncio`

## python example with semaphore

Python mysql example: example with semaphore

```python
import asyncio
from contextlib import closing
import random


async def async_index_printer(index: int):
    print('start', index)
    await asyncio.sleep(random.uniform(1, 3))
    return index


async def do_with_semaphore(semaphore: asyncio.Semaphore, future):
    async with semaphore:
        return await future


async def async_index_printer_with_finisher():
    semaphore = asyncio.Semaphore(2)
    futures = [do_with_semaphore(semaphore, async_index_printer(i)) for i in range(5)]
    for completed_future in asyncio.as_completed(futures):
        result = await completed_future
        print('end', result)


def main():
    with closing(asyncio.get_event_loop()) as loop:
        loop.set_debug(True)
        future = async_index_printer_with_finisher()
        loop.run_until_complete(future)


main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
