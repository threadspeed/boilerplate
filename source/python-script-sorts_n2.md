---
title: python script sorts n2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sorts n2'

Functions in program: 
* `def gnome_sort(a: list):`
* `def shaker_sort(a: list):`
* `def bubble_sort(a: list):`
* `def selection_sort(a: list):`

Modules used in program: 
* `import random`

## python sorts n2

Python example: sorts n2

```python
import random

def selection_sort(a: list):
    length = len(a)
    for i in range(length):
        current_min_i = i
        current_min = a[i]
        for j in range(i + 1, length):
            if a[j] < current_min:
                current_min = a[j]
                current_min_i = j
        a[i], a[current_min_i] = current_min, a[i]

def bubble_sort(a: list):
    length = len(a)
    for i in range(length):
        for j in range(i, length):
            if a[j] < a[i]:
                a[i], a[j] = a[j], a[i]

def shaker_sort(a: list):
    left = 0
    right = len(a) - 1
    while left <= right:
        for i in range(left, right):
            if a[i] > a[i + 1]:
                a[i], a[i + 1] = a[i + 1], a[i]
        right -= 1
        for i in range(right, left, -1):
            if a[i] < a[i - 1]:
                a[i], a[i - 1] = a[i - 1], a[i]
        left += 1

def gnome_sort(a: list):
    length = len(a)
    for i in range(1, length):
        j = i
        while j >= 1 and a[j] < a[j-1]:
            a[j], a[j-1] = a[j-1], a[j]
            j -= 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
