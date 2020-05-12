---
title: python script Ds coin (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds coin'


## python Ds coin

Python mysql example: Ds coin

```python
x = [[1] + [0]*9]

for i in range(100):
    this = [1]
    for j in range(1, 100):
        if j<=i:
            this.append(x[-1][j]+this[-1])
        else:
            this.append(0)
    x.append(this)

for i in range(99):
    print(x[i+1][i], end=' ')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
