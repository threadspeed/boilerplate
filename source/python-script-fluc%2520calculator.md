---
title: python script fluc%2520calculator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fluc%2520calculator'

Functions in program: 
* `def av(N, C):`
* `def flac(N):`

Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import time`
* `import random`

## python fluc%2520calculator

Python mysql example: fluc%2520calculator

```python
#   Amirkabir Univesity of Technology
#   Department of Physics
#   Random Processes Course
#   Behnood Bandi - Aria Naieni - Amir Kermanshahani

import random
import time
import matplotlib.pyplot as plt
import numpy as np

start = time.time()


def flac(N):
    n = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    i, j = 0, 0
    while i < N:
        a = random.randint(0, 10)
        n[a] = n[a] + 1
        i = i + 1

    while j < 11:
        n[j] = n[j] / N
        j = j + 1
    i, j = 0, 0
    k = 0
    f=max(n)-min(n)
    #while k < 11:
    #   b = b + (n[k] - min(n))
    #   k += 1
    #f = b / 2
    return (f)


def av(N, C):
    i = 0
    total = 0
    while i < C:
        total = total + flac(N)
        i += 1
    totalflac = total / C

    print('for', N, 'random: ')
    print(totalflac)
    end = time.time()
    print('time1=', end - start)
    return (totalflac)


N = [100, 500, 1000, 5000, 10000, 50000, 100000, 150000, 200000, 250000, 300000, 350000, 400000, 450000, 500000, 550000,
     600000, 650000, 700000, 750000, 800000, 850000, 900000, 950000, 1000000]
F = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

C = 100
i = 0
while i < len(N):
    F[i] = av(N[i], C)
    i += 1
print(N)
print(F)
end = time.time()
print('time=', end - start)

plt.plot(N,F)
plt. axhline(y=0,c='r')
plt.show()
np.savetxt("fluc3.csv", F, delimiter=",", fmt='%s')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
