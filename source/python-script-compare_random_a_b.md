---
title: python script compare random a b (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'compare random a b'

Functions in program: 
* `def read_data(filename):`

Modules used in program: 
* `import random`

## python compare random a b

Python mysql example: compare random a b

```python
#!/usr/bin/env python

"""Given two files that contain a list of data values, compute the
differences in the sample means with a bootstrapping approach
"""

import random

def read_data(filename):
    with open(filename) as stream:
        return map(float, stream.read().split())

m = 10000

a_data = read_data('sample_a.dat')
b_data = read_data('sample_b.dat')


# calculate how frequently a random a is greater than a random b
count = 0
for j in xrange(m):
    a = random.choice(a_data)
    b = random.choice(b_data)
    if a > b:
        count += 1

p_a_gt_b = float(count) / m
print("p(a > b) = %(p_a_gt_b)f" % locals())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
