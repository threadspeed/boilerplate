---
title: python script 1 pi estimate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '1 pi estimate'

Functions in program: 
* `def sample(p):`

## python 1 pi estimate

Python example: 1 pi estimate

```python
#!/usr/bin/python2.7
# Python map-reduce implementation
# Execution time for 10e8
# real	0m52.386s
# user	0m52.052s
# sys	0m0.008s
from random import random
NUM_SAMPLES = 10**8
def sample(p):
    x, y = random(), random()
    return 1 if x*x + y*y < 1 else 0

count = reduce(lambda a, b: a + b, (sample(x) for x in xrange(0, NUM_SAMPLES)))
print("Pi is roughly %f" % (4.0 * count / NUM_SAMPLES))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
