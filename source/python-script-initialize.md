---
title: python script initialize (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'initialize'


Modules used in program: 
* `import random`

## python initialize

Python mysql example: initialize

```python
# Nの乱数列を生成
import random
N = 100000
M = 100000
target = range(0,N)
temp = range(0,N)
for n in range(N-1,-1,-1):
  target[n] = temp.pop(random.randint(0,n))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
