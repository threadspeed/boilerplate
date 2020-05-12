---
title: python script sorter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sorter'

Functions in program: 
* `def partition(l, min, max):`
* `def sort(l):`

## python sorter

Python mysql example: sorter

```python
#!/usr/bin/env python
'''
Just another quicksort implementation, to see if I memorized the algorithmn.
Apparently, yes. :-)

Gotchas during the implementation:
- forgot to check min and max in the beginning, got IndexError
- choosing nonsense as pivot led me to almost-sorted list (worked when
I stopped being stupid)
'''

def sort(l):
    partition(l, 0, len(l) - 1)


def partition(l, min, max):
    if max <= min:
        return
    pivot = (max + min) // 2  # better if random, but I want to go bare
    pivot_value = l[pivot]
    l[pivot], l[max] = l[max], l[pivot]
    store = min
    for i in range(min, max):
        if l[i] <= pivot_value:
            l[i], l[store] = l[store], l[i]
            store += 1
    l[store], l[max] = l[max], l[store]
    partition(l, min, store -1)
    partition(l, store + 1, max)


if __name__ == '__main__':
    import random
    l = range(100000)
    random.shuffle(l)
    sort(l)
    assert l == sorted(l)
    print('sorted!')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
