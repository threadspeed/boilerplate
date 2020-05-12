---
title: python script timeit (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'timeit'

Functions in program: 
* `def findindict():`
* `def findintuple():`
* `def findinset():`
* `def findinlist():`

Modules used in program: 
* `import timeit`
* `import random`

## python timeit

Python example: timeit

```python
import random
import timeit

def findinlist():
    if searchvalue in lyst:
        return 1
    else:
        return 0
def findinset():
    if searchvalue in set1:
        return 1
    else:
        return 0
def findintuple():
    if searchvalue in tuple1:
        return 1
    else:
        return 0
def findindict():
    if searchvalue in dictionary1:
        return 1
    else:
        return 0

if __name__ == "__main__":
    global lyst
    lyst = random.sample(range(1,500),100)
    global set1
    set1 = set(lyst)
    global tuple1
    tuple1 = tuple(lyst)
    global dictionary1
    dictionary1 = {}
    for x in lyst:
        dictionary1[x] = x
    global searchvalue
    searchvalue = 3
    timelyst = timeit.timeit(findinlist)
    timeset = timeit.timeit(findinset)
    timetuple = timeit.timeit(findintuple)
    timedict = timeit.timeit(findindict)
    print("List search: ", timelyst)
    print("Set search: ", timeset)
    print("Tuple search: ", timetuple)
    print("Dictionary search: ", timedict)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
