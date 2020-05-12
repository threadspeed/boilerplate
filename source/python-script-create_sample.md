---
title: python script create sample (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create sample'

Functions in program: 
* `def write_sample(stream, n, lam):`

Modules used in program: 
* `import random`
* `import sys`

## python create sample

Python example: create sample

```python
#!/usr/bin/env python

"""I don't currently have access to the movie or horse racing data, so
use this script to create the group a and group b data sets that are
used in subsequent steps.
"""

import sys
import random

def write_sample(stream, n, lam):
    filename = stream.name
    sys.stderr.write((
        '%(filename)s with %(n)d values from exponential distribution'
        'with lam=%(lam)s\n'
    ) % locals())
    for i in xrange(n):
        x = random.expovariate(lam)
        stream.write(str(x) + '\n')

with open('sample_a.dat', 'w') as stream:
    write_sample(stream, 100000, 1.5)

with open('sample_b.dat', 'w') as stream:
    write_sample(stream, 20000, 1.1)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
