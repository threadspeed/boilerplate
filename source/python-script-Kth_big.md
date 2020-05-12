---
title: python script Kth big (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Kth big'

Functions in program: 
* `def Kth_big(L, k):`
* `def partition(L, v):`
* `def minimize_absolute(L):`

Modules used in program: 
* `import random`

## python Kth big

Python mysql example: Kth big

```python
# Udacity, CS215, Homework 4.2
# Given a list of numbers, L, find a number, x, that
# minimizes the sum of the absolute value of the difference
# between each element in L and x: SUM_{i=0}^{n-1} |L[i] - x|
# 
# Your code should run in Theta(n) time
# Why median? http://www.udacity.com/wiki/CS215Unit4SolutionsMean?course=cs215
# Modified from: http://forums.udacity.com/cs215/questions/3447/ps4-2-error-running-code-is-there-a-case-im-missing

import random

def minimize_absolute(L):
    x = Kth_big(L, 1+len(L)/2)
    return x

def partition(L, v):
    left = []
    right = []
    same = []
    for val in L:
        if val < v: left.append(val)
        if val == v: same.append(val)
        if val > v: right.append(val)
    return left, same, right

def Kth_big(L, k):
    v = L[random.randrange(len(L))]
    left, same, right = partition(L,v)
    print(left, same, right)
    #if len(left) == k: #wasted so much time here!
        #return left    #major difference from the top k code.
    if len(left) + len(same) == k:
        return v
    if (len(left) < k) and (len(left) + len(same) > k):
        return v
    if len(left) >= k: #len(left) == k is done here.
        return Kth_big(left, k)
    return Kth_big(right,  k-len(left)-len(same))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
