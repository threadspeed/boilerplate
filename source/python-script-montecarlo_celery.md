---
title: python script montecarlo celery (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'montecarlo celery'

Functions in program: 
* `def count_list(count):`
* `def map_d(c):`

Modules used in program: 
* `import math`
* `import random`
* `import itertools`

## python montecarlo celery

Python example: montecarlo celery

```python
import itertools
import random
import math

from celery import Celery
from celery import group

app = Celery('hello', broker='redis://localhost:6379/', backend='redis://localhost')


def map_d(c):
    return math.hypot(random.random(), random.random())


@app.task(name='count_list')
def count_list(count):
    d_list = itertools.imap(map_d, xrange(0, count))
    count_inside = sum(1 for d in d_list if d < 1)
    return count_inside


if __name__ == '__main__':
    count = 1000000
    tasks = 1000
    job = group(count_list.s(count) for i in range(0, tasks)).apply_async()
    count_list = job.get()
    total_count_inside = sum(count_list)

    print(4.0 * total_count_inside / (count * tasks))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
