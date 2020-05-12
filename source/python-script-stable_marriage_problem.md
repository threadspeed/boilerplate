---
title: python script stable marriage problem (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'stable marriage problem'

Functions in program: 
* `def randomPairsGen(size):                                                                                                                                                    [12/462]`
* `def stableMarriage(prefer):`
* `def wPrefersM1OverM(prefer, w, m, m1):`

Modules used in program: 
* `import random`
* `import time`

## python stable marriage problem

Python mysql example: stable marriage problem

```python
import time
import random

def wPrefersM1OverM(prefer, w, m, m1):
    for i in range(len(prefer)//2):
        if prefer[w][i] == m1:
            return True
        if prefer[w][i] == m:
            return False

def stableMarriage(prefer):
    N = len(prefer)//2
    wParter = [-1 for i in range(N)]
    mFree = [False for i in range(N)]

    freeCount = N

    while freeCount > 0:
        m = None
        for i in range(N):
            if mFree[i] == False:
                m = i
                break

        i = 0
        while i<N and mFree[m] == False:
            w = prefer[m][i]

            if wParter[w-N] == -1:
                wParter[w-N] = m
                mFree[m] = True
                freeCount -= 1
            else:
                m1 = wParter[w-N]

                if wPrefersM1OverM(prefer, w, m, m1) == False:
                    wParter[w-N] = m
                    mFree[m] = True
                    mFree[m1] = False
            i += 1
def randomPairsGen(size):                                                                                                                                                    [12/462]
    prefer = []
    for i in range(size):
        tmp = [i+size for i in range(size)]
        random.shuffle(tmp)
        prefer.append(tmp)
    for i in range(size):
        tmp = [i for i in range(size)]
        random.shuffle(tmp)
        prefer.append(tmp)
    return prefer

if __name__ == "__main__":
    random.seed(time.time())
    f0 = open("result_stable_marriage_100.csv", "w")
    f1 = open("result_stable_marriage_500.csv", "w")
    f2 = open("result_stable_marriage_1000.csv", "w")
    f3 = open("result_stable_marriage_2000.csv", "w")
    for idx in range(1000):
        prefer = randomPairsGen(100)
        start = time.time()*1000
        stableMarriage(prefer)
        end = time.time()*1000
        timeStamp = str(end - start)
        if idx != 999:
            timeStamp += ","
        f0.write(timeStamp)
        
        prefer = randomPairsGen(500)
        start = time.time()*1000
        stableMarriage(prefer)
        end = time.time()*1000
        timeStamp = str(end - start)
        if idx != 999:
            timeStamp += ","
        f1.write(timeStamp)
        
        prefer = randomPairsGen(1000)
        start = time.time()*1000
        stableMarriage(prefer)
        end = time.time()*1000
        timeStamp = str(end - start)
        if idx != 999:
            timeStamp += ","
        f2.write(timeStamp)

        prefer = randomPairsGen(2000)
        start = time.time()*1000
        stableMarriage(prefer)
        end = time.time()*1000
                timeStamp = str(end - start)
        if idx != 999:
            timeStamp += ","
        f3.write(timeStamp)
    f1.close()
    f2.close()
    f3.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
