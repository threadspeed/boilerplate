---
title: python script list solution (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'list solution'

Functions in program: 
* `def list_solution(values, collection):`
* `def timeit(func):`

Modules used in program: 
* `import sys`
* `import time`
* `import random`
* `import functools`

## python list solution

Python mysql example: list solution

```python

import functools
import random
import time
import sys


def timeit(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        response = func(*args, **kwargs)
        took = time.time() - start

        func_name = func.__name__
        print(f"{func_name} --> took {took:.2f} ")
        return response
    return wrapper


@timeit
def list_solution(values, collection):
    for value in values:
        assert value in collection
    

size = 30_000_000
collection = [x for x in range(size)]
collection_size_mb = sys.getsizeof(collection) / 1024 / 1024

print(f"Collection size: {collection_size_mb:.2f}mb")

values = [random.randint(0, size) for _ in range(100)]

list_solution(values, collection)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
