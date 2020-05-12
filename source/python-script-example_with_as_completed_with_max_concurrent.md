---
title: python script example with as completed with max concurrent (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'example with as completed with max concurrent'

Functions in program: 
* `def main():`

Modules used in program: 
* `import asyncio_helper`
* `import random`
* `import asyncio`

## python example with as completed with max concurrent

Python mysql example: example with as completed with max concurrent

```python
import asyncio
from contextlib import closing
import random

import asyncio_helper


async def async_index_printer(index: int):
    print('start', index)
    await asyncio.sleep(random.uniform(1, 3))
    return index


async def async_index_printer_with_finisher():
    futures = map(async_index_printer, range(5))
    # Use as_completed_with_max_concurrent instead of asyncio.as_completed.
    for completed_future in asyncio_helper.as_completed_with_max_concurrent(futures, max_concurrent=2):
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
