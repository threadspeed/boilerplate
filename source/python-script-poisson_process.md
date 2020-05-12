---
title: python script poisson process (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'poisson process'

Functions in program: 
* `def poisson(lda):`
* `def exp(lda):`

Modules used in program: 
* `import random as rn`
* `import math as m`

## python poisson process

Python example: poisson process

```python
import math as m
import random as rn


def exp(lda):
    while True:
        yield -m.log(rn.random())/lda


def poisson(lda):
    t = 0
    for dt in exp(lda):
        t += dt
        yield t
        
process = poisson(3)
for _ in range(10):
    print(next(process))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
