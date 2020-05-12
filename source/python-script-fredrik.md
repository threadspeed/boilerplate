---
title: python script fredrik (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fredrik'

Functions in program: 
* `def n(l,p=51):`

Modules used in program: 
* `import random as r`

## python fredrik

Python example: fredrik

```python
def n(l,p=51):
 if p: return l[p-1]==l[p] or n(l,p-1)
import random as r
S,N=range(13)*4,1e6
a=[0]*int(N)
print(map(n,map(lambda a:r.sample(S,52),a)).count(1)/N)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
