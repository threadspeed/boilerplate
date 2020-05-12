---
title: python script ALGORITHM LAB Quick sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Quick sort'

Functions in program: 
* `def quick_sort(a):`

Modules used in program: 
* `import time`

## python ALGORITHM LAB Quick sort

Python example: ALGORITHM LAB Quick sort

```python
# Quick Sort 1

from random import randint
import time
def quick_sort(a):
    less,equal,higher=[],[],[]
    if len(a)>1:
        pivot=a[0]
        for x in a:
            if x<pivot:
                less.append(x)
            elif x==pivot:
                equal.append(x)
            elif x>pivot:
                higher.append(x)
        return quick_sort(less)+equal+quick_sort(higher)
    else :
        return a
a=[randint(0,100) for i in range(int(input()))]
print(a)
start=time.clock()
print(quick_sort(a))
print(time.clock()-start)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
