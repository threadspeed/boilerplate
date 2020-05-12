---
title: python script SERIAL MONTE CARLO BIRTHDAY (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SERIAL MONTE CARLO BIRTHDAY'


Modules used in program: 
* `import time`
* `import random`

## python SERIAL MONTE CARLO BIRTHDAY

Python example: SERIAL MONTE CARLO BIRTHDAY

```python
"""Monte Carlo simulation to find probabilty of 2 people having same birthday in a
   group of people.
   APPROX TIME TAKEN: 36.1090919971 secs when NTRIALS = 1000000
"""

import random
import time

START = time.time()
NTRIALS = 1000000
NPEOPLE = 30

matches = 0
for trial in xrange(NTRIALS):
    taken = {}

    for person in xrange(NPEOPLE):
        day = random.randint(0,365)
        if day in taken:
            matches += 1
            break
        taken[day] = 1

print("RESULT = {0}").format(float(matches)/NTRIALS)
print("TIME TAKEN = {0}").format(time.time() - START)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
