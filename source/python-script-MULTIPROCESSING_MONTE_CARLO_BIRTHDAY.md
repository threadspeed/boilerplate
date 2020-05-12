---
title: python script MULTIPROCESSING MONTE CARLO BIRTHDAY (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MULTIPROCESSING MONTE CARLO BIRTHDAY'

Functions in program: 
* `def prob(time):`

Modules used in program: 
* `import multiprocessing`
* `import time`
* `import random`

## python MULTIPROCESSING MONTE CARLO BIRTHDAY

Python example: MULTIPROCESSING MONTE CARLO BIRTHDAY

```python
"""A program to find out the probabilty of 2 people having same birthday.
   This uses multiprocessing approach, in this case is very simple and naive.
   Done for educational purpose.
   TIME TAKEN : 17.4336278439 secs when NTRIALS = 1000000
"""

import random
import time
import multiprocessing

START = time.time()
NTRIALS = 1000000
NPEOPLE = 30
PROCS = NTRIALS / 3    #this implies PRCOCS * 3 = NTRIALS. Therefore we have to perform
                       #prob() three times to reach NTRIALS. So three processes are created.

#time is a dummy parameter
def prob(time):
    matches = 0
    for i in xrange(PROCS):
        taken = {}
        for person in xrange(NPEOPLE):
            day = random.randint(0,365)
            if day in taken:
                matches = matches + 1
                break
            taken[day] = 1
    
    return matches

if __name__ == '__main__':
    result = []
    pool = multiprocessing.Pool(processes = 3)
    result = pool.map(prob, xrange(3))   #three times created as PROCS = NTRIALS / 3
    
    print("RESULT = {0} in time {1}").format(float(sum(result))/NTRIALS, time.time() - START)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
