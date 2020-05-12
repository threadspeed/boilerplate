---
title: python script insertionsort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'insertionsort'

Functions in program: 
* `def insertion_sort(items):`

Modules used in program: 
* `import random`

## python insertionsort

Python example: insertionsort

```python
"""
Creates small lists first and compares those, gradually
adds one to list and compares that list, eventually
taking up the whole original list.
"""

def insertion_sort(items):
	""" Implementation of insertion sort """
	for i in range(1, len(items)):
		j = i
		while j > 0 and items[j] < items[j-1]:
			items[j], items[j-1] = items[j-1], items[j]
			j -= 1

import random

random_items = [random.randint(-50,100) for c in range(50)]

print('Before: ', random_items)
insertion_sort(random_items)
print
print('After: ', random_items)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
