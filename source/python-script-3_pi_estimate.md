---
title: python script 3 pi estimate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '3 pi estimate'


## python 3 pi estimate

Python example: 3 pi estimate

```python
#!/usr/bin/python2.7
# Pytohn classic implementation
# execution time for 10e8
# real	0m37.567s
# user	0m37.512s
# sys	0m0.004s
from random import random
NUM_SAMPLES = 10**8

count_pass = 0

for _ in xrange(0, NUM_SAMPLES):
    x, y = random(), random()
    if (x*x + y*y <= 1):
        count_pass += 1
print(4.0 * count_pass / NUM_SAMPLES)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
