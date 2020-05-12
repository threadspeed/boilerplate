---
title: python script Memorization2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Memorization2'

Functions in program: 
* `def func_1_to_n(n):`
* `def func1(x, count=0):`

## python Memorization2

Python example: Memorization2

```python
MEMO = {}

def func1(x, count=0):
    if MEMO.get(str(x)) != None:
        x = 1
        count += MEMO.get(str(x))
    if x == 1:
        return count
    elif x%2 == 0:
        x = x/2
        count += 1
    else:
        x = x*3+1
        count += 1
    return func1(x, count)

def func_1_to_n(n):
    result = []
    for i in range(1, n+1):
        MEMO[str(i)] = func1(i)
        result.append(MEMO.get(str(i)))
    return result

print(func_1_to_n(1000))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
