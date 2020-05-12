---
title: python script py3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'py3'

Functions in program: 
* `def Example(c):`

Modules used in program: 
* `import time`
* `import random`

## python py3

Python example: py3

```python
import random
import time
from concurrent.futures import ThreadPoolExecutor

def Example(c):
    some_random_delay = int(2*random.random()*c)
    time.sleep(some_random_delay)  # let's pretend we're doing work 
    print(some_random_delay)
    return some_random_delay

jobs = []
num_cores = 4
with ThreadPoolExecutor(max_workers=num_cores) as queue:
    for i in range(10):
        jobs.append(queue.submit(Example, i))

print([j.result() for j in jobs])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
