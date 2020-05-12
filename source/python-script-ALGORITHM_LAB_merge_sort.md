---
title: python script ALGORITHM LAB merge sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB merge sort'

Functions in program: 
* `def merge_sort(a):`
* `def merge(a,b):`

Modules used in program: 
* `import random`

## python ALGORITHM LAB merge sort

Python mysql example: ALGORITHM LAB merge sort

```python
# Merger Sort

import random
n=int(input("enter the number of numbers"))
a=[random.randint(0,100) for i in range(n)]
def merge(a,b):
    i,j,c=0,0,[]
    while((i<len(a)) and (j<len(b))):
        if (a[i]<b[j]):
            c.append(a[i])
            i=i+1
        else:
            c.append(b[j])
            j=j+1
    while(i<len(a)):
        c.append(a[i])
        i=i+1
    while(j<len(b)):
        c.append(b[j])
        j=j+1
    return c
def merge_sort(a):
    if(len(a)>1):
        a1=merge_sort(a[0:len(a)//2])
        b1=merge_sort(a[len(a)//2:])
        a=merge(a1,b1)
    return a
print(a)
print(merge_sort(a))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
