---
title: python script random%25202 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random%25202'


Modules used in program: 
* `import random`

## python random%25202

Python example: random%25202

```python
import random
n = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
N = 900000
i, j = 0, 0
while i < N:
    a = random.randint(0, 10)
    n[a] = n[a] + 1
    i = i + 1

while j < 11:
    n[j] = n[j] / N
    j = j + 1
i,j=0,0
print('For', N, 'random:')
print(n)
fluc = max(n) - min(n)
print('Fluc=', fluc)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
