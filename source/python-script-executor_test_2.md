---
title: python script executor test 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'executor test 2'

Functions in program: 
* `def my_sleep(n=1000):`

Modules used in program: 
* `import random`
* `import time`

## python executor test 2

Python mysql example: executor test 2

```python
"""
This one works fine. `ex.submit` and `as_completed` play nicely together
"""
import time
import random
from concurrent.futures import ThreadPoolExecutor, as_completed


def my_sleep(n=1000):
    ident = random.randint(0, 1000)
    print("Starting %s" % ident)
    time.sleep(n)
    print("Finished: %s" % ident)
    return ident


ex = ThreadPoolExecutor(max_workers=4)

res = [
    ex.submit(my_sleep, n) for n in [100, 3, 2, 100]
]

for t in as_completed(res):
    print('##### Done: %s' % t)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
