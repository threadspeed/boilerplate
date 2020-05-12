---
title: python script Memorization1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Memorization1'

Functions in program: 
* `def func_1_to_n(n):`
* `def func1(x):`

## python Memorization1

Python example: Memorization1

```python
count = 0

def func1(x):
    global count
    if x == 1:
        return count
    elif x%2 == 0:
        x = x/2
        count += 1
    else:
        x = x*3+1
        count += 1
    return func1(x)

def func_1_to_n(n):
    result = []
    for i in range(1, n+1):
        result.append(func1(i))
    return result

print(func_1_to_n(1000))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
