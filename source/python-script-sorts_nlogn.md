---
title: python script sorts nlogn (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sorts nlogn'

Functions in program: 
* `def merge_sort(a: list):`
* `def merge(a: list, b: list):`
* `def qsort1(a: list):`
* `def qsort(a: list):`

Modules used in program: 
* `import random`

## python sorts nlogn

Python example: sorts nlogn

```python
import random

def qsort(a: list):
    if len(a) < 2:
        return a
    pivot = random.choice(a)
    less = [n for n in a if n < pivot]
    equal = [n for n in a if n == pivot]
    great = [n for n in a if n > pivot]
    return qsort(less) + equal + qsort(great)

def qsort1(a: list):
    length = len(a)
    result = qsort(a)
    for i in range(length):
        a[i] = result[i]

def merge(a: list, b: list):
    a_len = len(a)
    b_len = len(b)
    result = [0] * (a_len + b_len)
    a_idx = 0
    b_idx = 0
    result_idx = 0
    while a_idx < a_len and b_idx < b_len:
      if a[a_idx] <= b[b_idx]:
        result[result_idx] = a[a_idx]
        a_idx += 1
      else:
        result[result_idx] = b[b_idx]
        b_idx += 1
      result_idx += 1
    while a_idx < a_len:
      result[result_idx] = a[a_idx]
      a_idx += 1
      result_idx += 1
    while b_idx < b_len:
      result[result_idx] = b[b_idx]
      b_idx += 1
      result_idx += 1
    return result

def merge_sort(a: list):
    length = len(a)
    if length < 2:
      return a
    middle_idx = length // 2
    left_part = a[:middle_idx]
    right_part = a[middle_idx:]
    merge_sort(left_part)
    merge_sort(right_part)
    result = merge(left_part, right_part)
    for i in range(length):
      a[i] = result[i]


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
