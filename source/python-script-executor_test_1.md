---
title: python script executor test 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'executor test 1'

Functions in program: 
* `def my_sleep(n=1000):`

Modules used in program: 
* `import random`
* `import time`

## python executor test 1

Python example: executor test 1

```python
"""
This one "Doesn't" work. Seems like `map` doesn't play well with
`as_completed`.
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
res = ex.map(my_sleep, [1000, 3, 2, 1000])

for t in as_completed(res):
    print('##### Done: %s' % t)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
