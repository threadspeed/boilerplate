---
title: python script n-error (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'n-error'

Functions in program: 
* `def main():`
* `def dis(x, y):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import random`

## python n-error

Python mysql example: n-error

```python
# coding:utf-8
from __future__ import division

import random

import numpy as np
import matplotlib.pyplot as plt


def dis(x, y):
    return np.sqrt(x**2 + y**2)


def main():
    M = int(4e4)
    pi_n = np.zeros(M)
    count_inner = 0
    for n in range(M):
        x = random.random()
        y = random.random()
        if dis(x, y) < 1:
            count_inner += 1
        pi_n[n] = count_inner / (n + 1) * 4
    error = pi_n - np.pi
    error = np.abs(error)
    plt.plot(error)
    plt.ylabel('Error')
    plt.xlabel('n')
    plt.show()

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
