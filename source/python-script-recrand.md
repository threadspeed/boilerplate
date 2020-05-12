---
title: python script recrand (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'recrand'

Functions in program: 
* `def ranstr(n):`

Modules used in program: 
* `import random`

## python recrand

Python mysql example: recrand

```python
import random
def ranstr(n):
  s = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'
  if n == 0:
    return ""
  return s[random.randrange(0, len(s))] + ranstr(n-1)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
