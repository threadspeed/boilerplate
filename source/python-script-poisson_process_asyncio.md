---
title: python script poisson process asyncio (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'poisson process asyncio'

Functions in program: 
* `def exp(lda):`

Modules used in program: 
* `import string`
* `import random as rn`
* `import math as m`
* `import asyncio`

## python poisson process asyncio

Python mysql example: poisson process asyncio

```python
import asyncio
import math as m
import random as rn
import string


def exp(lda):
    while True:
        yield -m.log(rn.random())/lda


async def poisson(id="a", lda=0.3):
    for n, dt in enumerate(exp(lda), 1):
        await asyncio.sleep(dt)
        print("Event from {}, events up to now: {}".format(id, n)) 


loop = asyncio.get_event_loop()

for label in string.ascii_lowercase:
    loop.create_task(poisson(id=label))

loop.run_forever()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
