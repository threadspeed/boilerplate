---
title: python script gistfile2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gistfile2'

Functions in program: 
* `def select(seq, k):`
* `def partition(seq):`

## python gistfile2

Python mysql example: gistfile2

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-


def partition(seq):
    pi, seq = seq[0], seq[1:]         # Pick and remove the pivot
    lo = [x for x in seq if x <= pi]  # All the small elements
    hi = [x for x in seq if x > pi]   # All the large ones
    return lo, pi, hi                 # pi is "in the right place"


def select(seq, k):
    lo, pi, hi = partition(seq)
    m = len(lo)
    if m == k:
        return pi
    elif m < k:
        return select(hi, k-m-1)
    else:
        return select(lo, k)

if __name__ == "__main__":
    import random
    # 产生不重复的数
    A = range(0, 1000)
    random.shuffle(A)
    print(select(A, 100))
    import timeit
    from functools import partial
    t1 = timeit.Timer(partial(select, A, 100)).timeit(1000)
    print(t1)
    import cProfile
    cProfile.run('select(A, 100)')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
