---
title: python script logestic%2520map%25202 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'logestic%2520map%25202'

Functions in program: 
* `def logestic (mu,n,x0):`

Modules used in program: 
* `import math`
* `import random`
* `import matplotlib as plt`
* `import numpy as np`

## python logestic%2520map%25202

Python example: logestic%2520map%25202

```python
import numpy as np
import matplotlib as plt
import random
import math

def logestic (mu,n,x0):
    i=0
    x=x0
    while i<=n:
        x=mu*x*(1-x)
        i+=1
    return x
mu = np.arange(3, 4.01, 0.01)
n=5
x0 = 0.1
x = np.zeros(102)
i=0

while(i<100):
        x[i]=logestic(mu[i],n,x0)
        i+=1

np.savetxt("logestic.csv", x, delimiter=",", fmt='%s')
np.savetxt("mu.csv",mu,delimiter=",", fmt='%s')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
