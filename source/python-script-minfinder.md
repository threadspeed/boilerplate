---
title: python script minfinder (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'minfinder'

Functions in program: 
* `def pythonmin():`
* `def pythonmintostore():`
* `def findmin():`
* `def findmintostore():`

Modules used in program: 
* `import timeit`
* `import random`

## python minfinder

Python mysql example: minfinder

```python
#minfinder
import random
import timeit

def findmintostore():
    min1 = lyst[0]
    for x in lyst:
        if x < min1:
            min1 = x
    myminvalues.append(min1)
    
def findmin():
    min1 = lyst[0]
    for x in lyst:
        if x < min1:
            min1 = x

def pythonmintostore():
    min2 = min(lyst)
    pyminvalues.append(min2)

def pythonmin():
    min2 = min(lyst)
    
if __name__ == "__main__":
    global lyst
    lyst = random.sample(range(1,5000),1000)
    global mymin
    mymin = []
    global myminvalues
    myminvalues = []
    global pymin
    pymin = []
    global pyminvalues
    pyminvalues = []
    
    findmintostore()
    pythonmintostore()
    
    time = timeit.timeit(findmin)
    mymin.append(time)
    
    time2 = timeit.timeit(pythonmin)
    pymin.append(time2)
    print(mymin)
    print(pymin)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
