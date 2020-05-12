---
title: python script top k (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'top k'

Functions in program: 
* `def top_k(L, k):`
* `def partition(L, p):`
* `def top_k(L, k):`
* `def partition(L, v):`

Modules used in program: 
* `import random`
* `import random`

## python top k

Python mysql example: top k

```python
# Udacity, CS215, 3.16-3.18 Top K Code
# The original version: http://www.udacity.com/wiki/CS215Unit4?course=cs215
# No equal elements in the list

import random

L = [31, 45, 91, 51, 66, 82, 28, 33, 11, 89, 27, 36]

def partition(L, v):
    smaller = []
    bigger = []
    for val in L:
        if val < v: smaller += [val]
        if val > v: bigger += [val]
    return (smaller, [v], bigger)

print(partition(L, 84))
# >>>[31, 45, 51, 66, 82, 28, 33, 11, 27, 36, 84, 91, 89]

def top_k(L, k):
    v = L[random.randrange(len(L))]
    (left, middle, right) = partition(L, v)
    # middle used below (in place of [v]) for clarity
    if len(left) == k:   return left
    if len(left)+1 == k: return left + middle
    if len(left) > k:    return top_k(left, k)
    return left + middle + top_k(right, k - len(left) - len(middle))

print(top_k(L, 5))
# >>> [31, 28, 33, 11, 27]
# list order may vary due to random selection of v


# Modified version of Top K Code 
# Consider the equal elements in the list.

import random

def partition(L, p):
    return [l for l in L if l<p], [l for l in L if l==p], [l for l in L if l>p]

def top_k(L, k):
    p = L[random.randrange(len(L))]
    left, same, right = partition(L, p)
    #print(left, same, right)
    if len(left) == k:
        return left
    if len(left) + len(same) == k:
        return left + same
    if len(left) < k and (len(left) + len(same)) > k:
        return left + [p]*(k - len(left))
    if len(left) > k:
        return top_k(left, k)
    return left + same + top_k(right, k-len(left)-len(same))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
