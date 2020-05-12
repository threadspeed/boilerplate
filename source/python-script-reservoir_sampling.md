---
title: python script reservoir sampling (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reservoir sampling'

Functions in program: 
* `def reservoir_sampling(file_handle, N=1000000, callable=None):`

Modules used in program: 
* `import random`

## python reservoir sampling

Python example: reservoir sampling

```python
import random

def reservoir_sampling(file_handle, N=1000000, callable=None):
    sample = []

    if callable is None:
        callable = lambda x: x

    for n, line in enumerate(file_handle):
        if n < N:
            sample.append(callable(line))
        elif n >= N and random.random() < N/float(n+1):
            replace = random.randint(0,len(sample)-1)
            sample[replace] = callable(line)
    return sample

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
