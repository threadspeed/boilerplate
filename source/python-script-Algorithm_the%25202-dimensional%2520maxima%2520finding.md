---
title: python script Algorithm the%25202-dimensional%2520maxima%2520finding (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Algorithm the%25202-dimensional%2520maxima%2520finding'

Functions in program: 
* `def Recursion_Point(array,i,j):`
* `def Recursion(array):`
* `def brute_force(array):`

Modules used in program: 
* `import time`
* `import random`
* `import cProfile`

## python Algorithm the%25202-dimensional%2520maxima%2520finding

Python example: Algorithm the%25202-dimensional%2520maxima%2520finding

```python
import cProfile
import random
import time


def brute_force(array):
    ary = array.copy()
    for i in ary:
        for j in ary:
            if j[0]<i[0] and j[1]<i[1]:
                if j in array : array.remove(j)
    return array

def Recursion(array):
    if len(array) == 1 :return array
    mid = int(len(array)/2)
    left = Recursion(array[:mid])
    right = Recursion(array[mid:])
    left =[i for i in left if i[1]>=right[0][1]]
    return left + right

def Recursion_Point(array,i,j):
    if i==j :return [array[i]]
    mid = int((i+j)/2)
    left = Recursion_Point(array,i,mid)
    right = Recursion_Point(array,mid+1,j)
    left =[i for i in left if i[1]>=right[0][1]]
    return left + right



array = []
n = 1000000
for i in range(n):array.append((random.randint(0,10000),random.randint(0,10000)))
array = list(set(array))
array.sort(key=lambda x:x[0])

'''cProfile.run('brute_force(array)')'''
cProfile.run('Recursion(array)')
cProfile.run('Recursion_Point(array,0,len(array)-1)')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
