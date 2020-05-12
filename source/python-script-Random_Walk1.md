---
title: python script Random Walk1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random Walk1'

Functions in program: 
* `def lenth():`
* `def randwalk():`

Modules used in program: 
* `import random`
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python Random Walk1

Python mysql example: Random Walk1

```python
import numpy as np
import matplotlib.pyplot as plt
import random

def randwalk():
    r = random.randint(1,2)
    if r == 1:
        di=-1
    else:
        di=1
    return di
def lenth():
    l = random.random()
    return l

N=100000000
M=100
x = np.zeros((M,N))
x2 = np.zeros((M,N))
avx=np.zeros(M)
avx2=np.zeros(M)
for k in range (0,M):

    for i in range (1,N):
        l=lenth()
        x[k][i]=x[k][i-1]+l*randwalk()
        x2[k][i]=x2[k][i-1]+x[k][i]**2
    avx,avx2=0,0
for w in range (0,M):
    for p in range(0,N):
        avx[w]=avx[w]+x[w][p]
        avx2[w]=avx2[w]+x2[w][p]

for h in range (0,M):
    avx[h]=avx[h]/N
    avx2[h]=avx2[h]/N
plt.plot(x[1])
plt.show()
plt.plot(x2[1])
plt.show()
plt.plot(avx)
plt.show()
plt.plot(avx2)
plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
