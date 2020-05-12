---
title: python script montecarlo futures (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'montecarlo futures'

Functions in program: 
* `def reduce_d(count_inside, d):`
* `def map_d(c):`

Modules used in program: 
* `import math`
* `import random`
* `import itertools`

## python montecarlo futures

Python mysql example: montecarlo futures

```python
from concurrent import futures
import itertools
import random
import math

def map_d(c):
    return math.hypot(random.random(), random.random())

def reduce_d(count_inside, d):
	if d < 1:
		return count_inside + 1

	return count_inside

count = 100000
with futures.ProcessPoolExecutor(max_workers=4) as executor:
    d_list = executor.map(map_d, xrange(0, count))
    count_inside = sum(1 for d in d_list if d < 1)

print(4.0 * count_inside / count)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
