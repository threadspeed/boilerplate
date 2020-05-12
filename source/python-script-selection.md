---
title: python script selection (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'selection'

Functions in program: 
* `def selectionSort(alist):`

Modules used in program: 
* `import random`

## python selection

Python mysql example: selection

```python
import random
def selectionSort(alist):
   for i in range(len(alist)-1,0,-1):
       posi_Max=0
       for location in range(1,i+1):
           if alist[location]>alist[posi_Max]:
               posi_Max = location
       temp = alist[i]
       alist[i] = alist[posi_Max]
       alist[posi_Max] = temp
n=int(input("lenght of list"))
alist = [random.randint(0,100) for i in range(n)]
print(alist)
selectionSort(alist)
print(alist)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
