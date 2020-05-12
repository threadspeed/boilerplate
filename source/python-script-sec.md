---
title: python script sec (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sec'

Functions in program: 
* `def median(thelist):`

## python sec

Python example: sec

```python
def median(thelist):
    median = 0
    sortedlist = sorted(thelist)
    lengthofthelist = len(sortedlist)
    centerofthelist = lengthofthelist / 2
    if len(sortedlist) % 2 == 0:
        temp = 0.0
        medianparties = []
        medianparties = sortedlist[centerofthelist -1 : centerofthelist +1 ]
        for value in medianparties:
            temp += value
            median = temp / 2
        return median
    else:
        return sortedlist[centerofthelist]

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
