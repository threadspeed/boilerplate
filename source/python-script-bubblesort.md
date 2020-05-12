---
title: python script bubblesort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bubblesort'

Functions in program: 
* `def bubble_sort(items):`

Modules used in program: 
* `import random`

## python bubblesort

Python example: bubblesort

```python
"""
Bubble sort compares adjacent items in a list and
swaps them depending on which item is greater. 
The reason why the inner for loop says
for j in range(len(items)-1-i)
is because the size of items to evaluate decreases by 1
per iteration. The greatest is already determined in the first iteration.
"""
def bubble_sort(items):
	""" Implementation of bubble sort """
	for i in range(len(items)):
		for j in range(len(items)-1-i):
			if items[j] > items[j+1]:
				items[j], items[j+1] = items[j+1], items[j]

import random

random_items = [random.randint(-50, 100) for c in range(50)]

print('Before: ', random_items)
bubble_sort(random_items)
print()
print('After: ', random_items)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
