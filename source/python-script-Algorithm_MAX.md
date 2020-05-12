---
title: python script Algorithm MAX (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Algorithm MAX'

Functions in program: 
* `def Max_DividePoint(i,j,array):`
* `def Max_Divide(array):`
* `def Max_For(array):`

Modules used in program: 
* `import random`
* `import time`
* `import cProfile`

## python Algorithm MAX

Python mysql example: Algorithm MAX

```python
import cProfile
import time
import random


def Max_For(array):
    a = array[0]
    for i in array[1:]:
        if i > a : a = i
    return a

def Max_Divide(array):
    if len(array)==1:return array[0]
    mid = int(len(array)/2)
    return max(Max_Divide(array[:mid]),Max_Divide(array[mid:]))

def Max_DividePoint(i,j,array):
    if i==j :return  array[i]
    if i==j-1 : return max(array[i],array[j])
    mid = int((j+i)/2)
    return max(Max_DividePoint(i,mid,array),Max_DividePoint(mid+1,j,array))

array = []
n = 1000000
for i in range(n):
    array.append(random.randint(0,n))

'''cProfile.run('Max_For(array)')'''
cProfile.run('Max_Divide(array)')
cProfile.run('Max_DividePoint(0,len(array)-1,array)')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
