---
title: python script py2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'py2'

Functions in program: 
* `def Example(c):`

Modules used in program: 
* `import time`
* `import random`

## python py2

Python mysql example: py2

```python
import random
from joblib import Parallel, delayed
import time

def Example(c):
    some_random_delay = int(2*random.random()*c)
    time.sleep(some_random_delay)  # let's pretend we're doing work 
    print(some_random_delay)
    return some_random_delay

num_cores = 4
jobs = Parallel(n_jobs=num_cores)(delayed(Example)(i) for i in range(10))
print(jobs)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
