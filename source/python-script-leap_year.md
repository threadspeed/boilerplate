---
title: python script leap year (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'leap year'

Functions in program: 
* `def is_leap(year):`

## python leap year

Python mysql example: leap year

```python
# https://www.hackerrank.com/challenges/write-a-function/problem


def is_leap(year):
    leap = False
    if year in (2000, 2400):
        return True

    if year % 4 == 0 and (year % 100 != 0 or year % 400 == 0):
        leap = True

    return leap


print(is_leap(2019))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
