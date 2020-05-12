---
title: python script MergeSort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MergeSort'

Functions in program: 
* `def Merge(A,p,q,r):`
* `def MergeSort(A,p,r):`

Modules used in program: 
* `import random`
* `import time`

## python MergeSort

Python mysql example: MergeSort

```python
MAX = 10000000

def MergeSort(A,p,r):
    if p < r:
        q = int((p+r)/2)
        MergeSort(A,p,q)
        MergeSort(A,q+1,r)
        Merge(A,p,q,r)


def Merge(A,p,q,r):
    global MAX
    L = A[p:q+1]+[MAX]
    R = A[q+1:r+1]+[MAX]
    i = 0
    j = 0
    for k in range(p,r+1):
        if L[i] <= R[j]:
            A[k] = L[i]
            i += 1
        else:
            A[k] = R[j]
            j += 1

import time
import random
a = time.time()
A = [random.randrange(10000000) for i in range(1000000)]
MergeSort1(A,0,len(A)-1)
b = time.time()
print("Done in "+str(b-a)+" secs")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
