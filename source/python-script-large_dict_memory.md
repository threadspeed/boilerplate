---
title: python script large dict memory (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'large dict memory'


Modules used in program: 
* `import gc`
* `import random`

## python large dict memory

Python mysql example: large dict memory

```python
import random
import gc

from memory_profiler import memory_usage

large_dict = {}
for x in xrange(50000):
	large_row = {}
	for y in xrange(125):
		large_row[random.randint(1, 10000000000)] = random.randint(1, 10000000000)
	large_dict[random.randint(1, 10000000000)] = large_row

large_dict = {}
del large_dict
gc.collect()

print(memory_usage(-1, interval=.2, timeout=1), "after gc.collect()")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
