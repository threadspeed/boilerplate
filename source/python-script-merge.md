---
title: python script merge (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'merge'

Functions in program: 
* `def merge(list1, list2):`

Modules used in program: 
* `import random`

## python merge

Python mysql example: merge

```python
import random

def merge(list1, list2):
    i, j = 0, 0
    list3 = []

    while i < len(list1) and j < len(list2):
        if list1[i] <= list2[j]:
            list3.append(list1[i])
            i += 1
        else:
            list3.append(list2[j])
            j += 1

    if i < len(list1): list3.extend(list1[i:])

    if j < len(list2): list3.extend(list2[j:])

    return list3
        

if __name__ == '__main__':
    a = sorted([random.randint(0, 10) for i in range(5)])
    b = sorted([random.randint(0, 10) for i in range(10)])
    c = merge(a, b)
    print(a)
    print(b)
    print(c)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
