---
title: python script TimingFindingMin (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'TimingFindingMin'

Functions in program: 
* `def myMin(lyst):`

Modules used in program: 
* `import time`
* `import random`

## python TimingFindingMin

Python example: TimingFindingMin

```python
import random
import time
def myMin(lyst):
    mMin = lyst[0]
    for x in range(1,len(lyst)):
        if lyst[x] < mMin:
            mMin = lyst[x]
    return mMin
myMinNum = 0
pyMinNum = 0
myPastTime = 0
pyPastTime = 0
myTotalTime = 0
pyTotalTime = 0
timesRan = 0
lastTime = 0
for x in range(10000):
    lyst = random.sample(range(1,500000000), 100)
    lastTime = time.time()
    myMinNum = myMin(lyst)
    myPastTime = time.time() - lastTime
    
    lastTime = time.time()
    pyMinNum = min(lyst)
    pyPastTime = time.time() - lastTime

    
    if myMinNum == pyMinNum:
        myTotalTime += myPastTime
        pyTotalTime += pyPastTime
        timesRan += 1

print("my time is " + str(myTotalTime / timesRan))
print("python's time is " + str(pyTotalTime / timesRan))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
