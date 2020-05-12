---
title: python script initializeA (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'initializeA'


Modules used in program: 
* `import random`

## python initializeA

Python mysql example: initializeA

```python
# Nの乱数列を生成
import random
N = 1000000
M = 40000
target = range(0,N)
for n in range(N-1,-1,-1):
  target[n] = random.randint(0,M-1)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
