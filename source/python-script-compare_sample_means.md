---
title: python script compare sample means (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'compare sample means'

Functions in program: 
* `def calculate_sample_mean(n, data):`
* `def read_data(filename):`

Modules used in program: 
* `import random`

## python compare sample means

Python mysql example: compare sample means

```python
#!/usr/bin/env python

"""Given two files that contain a list of data values, compute the
differences in the sample means with a bootstrapping approach
"""

import random

def read_data(filename):
    with open(filename) as stream:
        return map(float, stream.read().split())

def calculate_sample_mean(n, data):
    sample = [random.choice(data) for i in xrange(n)]
    return sum(sample) / n

m = 1000
n = 100

a_data = read_data('sample_a.dat')
b_data = read_data('sample_b.dat')


# calculate a bunch of sample means
count = 0
for j in xrange(m):
    a_mean = calculate_sample_mean(n, a_data)
    b_mean = calculate_sample_mean(n, b_data)
    if a_mean > b_mean:
        count += 1

print("a_mean > b_mean %(count)d out of %(m)d times" % locals())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
