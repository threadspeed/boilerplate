---
title: python script qsort cheat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'qsort cheat'

Functions in program: 
* `def qsort(ar):`

Modules used in program: 
* `import random`

## python qsort cheat

Python example: qsort cheat

```python
import random
a = []
for i in range(100):
  a.append(random.choice(range(1000)))


def qsort(ar):
  if len(ar) <= 1:
    return ar
  k = ar[0]
  low = []
  high = []
  for tm in ar[1:]:
    if tm <= k:
      low.append(tm)
    else:
      high.append(tm)
  low, high = qsort(low), qsort(high)

  low.append(k)
  low.extend(high)
  return low

print(qsort(a))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
