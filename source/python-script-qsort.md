---
title: python script qsort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'qsort'

Functions in program: 
* `def qsort(ar, min_, max_):`

Modules used in program: 
* `import random`

## python qsort

Python mysql example: qsort

```python
import random
a = []
for i in range(100):
  a.append(random.choice(range(1000)))


def qsort(ar, min_, max_):
  if len(ar) <= 1:
    return ar
  if min_ >= max_:
  	return ar
  k = ar[0]
  i, j = min_, max_
  while i<j:
  	while j > i and ar[j] > k:
    	j -= 1
    if j > i:
    	ar[i] = a[j]
    while i < j and ar[i] < k:
    	i += 1
    if j > i:
    	ar[j] = ar[i]
    ar[i] = k
  
  qsort(ar, min_, i-1)
  qsort(ar, i+1, max_)
  return low

print(qsort(a))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
