---
title: python script untriv sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untriv sort'

Functions in program: 
* `def untriv_sort(l: list, depth=1) -> list:`

Modules used in program: 
* `import random`

## python untriv sort

Python mysql example: untriv sort

```python
import random


def untriv_sort(l: list, depth=1) -> list:
    a = [[] for i in range(0, 10)]
    is_more = False
    for n in l:
        if n // (10 ** depth) != 0:
            is_more = True
        # print(n // (10 * (depth-1) or 1) % (10 * depth))
        a[n // (10 ** (depth-1) or 1) % 10].append(n)

    m = []
    for i in a:
        for n in i:
            m.append(n)

    # print(a)
    # print(m)
    # print()

    if is_more:
        return untriv_sort(m, depth+1)
    else:
        return m

a = [random.randrange(0, 1000) for i in range(1, 11)]

print(a)

s = untriv_sort(a)

is_valid = True
for i in range(1, len(s)):
    if s[i] < s[i-1]:
        is_valid = False
        break

print(f'{s} - {is_valid} - {s == sorted(a)}')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
