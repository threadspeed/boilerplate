---
title: python script sleep (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sleep'


Modules used in program: 
* `import time`
* `import gc`
* `import random`

## python sleep

Python mysql example: sleep

```python
import random
import gc
import time

large_dict = {}
for x in xrange(50000):
	large_row = {}
	for y in xrange(125):
		large_row[random.randint(1, 10000000000)] = random.randint(1, 10000000000)
	large_dict[random.randint(1, 10000000000)] = large_row

	
# Force a sweep
large_dict = {}
del large_dict
gc.collect()

time.sleep(55000)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
