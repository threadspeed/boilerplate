---
title: python script linearsearch (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'linearsearch'

Functions in program: 
* `def linear_search(lst, item):`

Modules used in program: 
* `import random`

## python linearsearch

Python example: linearsearch

```python
def linear_search(lst, item):
  found = False
  position = 0
  
  while position < len(lst) and not found:
    if lst[position] == item:
      found = True
      return "Found at position {}".format(position)
    position += 1

import random

lst = [random.randint(-50,100) for c in range(30)]
item = 203
lst[random.randint(0,29)] = item

print(lst)
print(linear_search(lst, item))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
