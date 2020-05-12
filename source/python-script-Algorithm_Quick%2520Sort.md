---
title: python script Algorithm Quick%2520Sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Algorithm Quick%2520Sort'

Functions in program: 
* `def Quick_Sort(ary):`

## python Algorithm Quick%2520Sort

Python example: Algorithm Quick%2520Sort

```python
def Quick_Sort(ary):
    if len(ary) < 2:
        return ary
    pivot =  [ary[0]]
    leftary = [i for i in ary if i < pivot[0]]
    rightary = [i for i in ary if i > pivot[0]]
    return Quick_Sort(leftary) + pivot + Quick_Sort(rightary)


print(Quick_Sort([1,5,9,8,7,6,5,4]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
