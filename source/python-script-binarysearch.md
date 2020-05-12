---
title: python script binarysearch (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'binarysearch'

Functions in program: 
* `def binary_search(items, el):`

## python binarysearch

Python example: binarysearch

```python
def binary_search(items, el):
	first = 0
	last = len(items) - 1
	found = False

	while first <= last and not found:
		mid = (first + last) // 2
		if items[mid] == el:
			found = True
		else:
			if el < items[mid]:
				last = mid - 1
			else:
				first = mid + 1

	return found
items = [2, 3, 4, 5, 6, 17, 19, 23, 100,102, 204, 301, 651]
print(binary_search(items, 17))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
