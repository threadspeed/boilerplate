---
title: python script montecarlo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'montecarlo'

Functions in program: 
* `def reduce_d(count_inside, d):`
* `def map_d(c):`

Modules used in program: 
* `import math`
* `import random`
* `import itertools`

## python montecarlo

Python example: montecarlo

```python
import itertools
import random
import math

def map_d(c):
	return math.hypot(random.random(), random.random())

def reduce_d(count_inside, d):
	if d < 1:
		return count_inside + 1

	return count_inside

count = 100000000
d_list = itertools.imap(map_d, xrange(0, count))
count_inside = reduce(reduce_d, d_list )

print(4.0 * count_inside / count)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
