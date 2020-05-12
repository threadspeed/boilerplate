---
title: python script Algorithm sum (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Algorithm sum'

Functions in program: 
* `def sumT(ary):`
* `def sumFor(ary):`
* `def sumRecursion(ary):`

Modules used in program: 
* `import cProfile`
* `import time`

## python Algorithm sum

Python mysql example: Algorithm sum

```python
import time
import cProfile

def sumRecursion(ary):
    if len(ary) == 1:
        return ary[0]
    return ary[0] + sum(ary[1:])

def sumFor(ary):
    sum = 0
    for i in ary:
        sum +=i
    return sum

def sumT(ary):
    return (0 + ary[-1] * len(ary))/2


ary = []
for i in range(100000):
    ary.append(i)

print(sumRecursion(ary))
cProfile.run('sumRecursion(ary)')
print(sumFor(ary))
cProfile.run('sumFor(ary)')
print(sumT(ary))
cProfile.run('sumT(ary)')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
