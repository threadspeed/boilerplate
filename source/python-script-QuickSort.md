---
title: python script QuickSort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'QuickSort'

Functions in program: 
* `def RandomizedPartition(A,p,r):`
* `def Partition(A,p,r):`
* `def QuickSort(A,p,r):`

Modules used in program: 
* `import time`
* `import random`

## python QuickSort

Python mysql example: QuickSort

```python
import random

def QuickSort(A,p,r):
    if p<r:
        q = Partition(A,p,r)
        QuickSort(A,p,q-1)
        QuickSort(A,q+1,r)

def Partition(A,p,r):
    x = A[r]
    i = p - 1
    for j in range(p,r):
        if A[j] <= x:
            i = i + 1
            A[i], A[j] = A[j], A[i]
    A[i+1], A[r] = A[r], A[i+1]
    return i+1

def RandomizedPartition(A,p,r):
    i = random.randrange(p,r+1)
    A[i],A[r] = A[r], A[i]
    return Partition(A,p,r)

import time
a = time.time()
A = [random.randrange(10000000) for i in range(1000000)]
QuickSort(A,0,len(A)-1) 
b = time.time()
print("Done in "+str(b-a)+" secs")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
