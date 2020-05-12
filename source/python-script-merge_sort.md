---
title: python script merge sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'merge sort'

Functions in program: 
* `def merge_sort(a, s=0, e=None):`

Modules used in program: 
* `import random`

## python merge sort

Python mysql example: merge sort

```python
import random


def merge_sort(a, s=0, e=None):
    if not e:
        e = len(a) - 1

    if e - s == 0:
        return [a[s]]
    elif e - s == 1:
        es = [a[s], a[e]]
        return [min(es), max(es)]
    else:
        m = s + (e - s) // 2  # Find the middle element id
        f = merge_sort(a, s, m)  # The 1st half
        l = merge_sort(a, m+1, e)  # The 2nd half
        # print(f'[{s}; {m}] [{m+1}; {e}]\n{f}\n{l}\n')
        n = []  # The final list
        while f or l:  # While sorted f and l have elements
            if f and l:  # If both f and l lists have elements
                # Compare first elements of the f and l lists
                # Add a lesser element to the final list
                # and remove it from the l or f list
                n.append(l.pop(0) if f[0] > l[0] else f.pop(0))
            elif l:
                n.append(l.pop(0))  # If f is empty then add number from the l list
            elif f:
                n.append(f.pop(0))  # If l is empty then add element from the f list
        return n


a = [random.randrange(1, 101) for i in range(1, 11)]

print(a)

s = merge_sort(a)

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
