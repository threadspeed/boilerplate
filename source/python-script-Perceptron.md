---
title: python script Perceptron (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Perceptron'


Modules used in program: 
* `import random`
* `import numpy as np`
* `import matplotlib.pyplot as mp`

## python Perceptron

Python mysql example: Perceptron

```python
#! python3
#
#Credits : https://blog.dbrgn.ch/2013/3/26/perceptrons-in-python/
#
import matplotlib.pyplot as mp
import numpy as np
import random
mp.ion()
fig=mp.figure()
mp.axis([0,100,-1,2])
data = [
    (np.array([0,0,1]), 0),
    (np.array([0,1,1]), 1),
    (np.array([1,0,1]), 1),
    (np.array([1,1,1]), 1),
]
w = np.random.rand(3)
unit_step = lambda x: 0 if x < 0 else 1
errors = []
lr=0.1
epoch=100
for i in range(epoch):
    x, expected = random.choice(data)
    result = np.dot(w, x)
    error = expected - unit_step(result)
    errors.append(error)
    w += lr * error * x
    ssa=w
    mp.plot(i, error,'m.')
    mp.plot(i, ssa[0],'g.')
    mp.plot(i, ssa[1],'r.')
    mp.plot(i, ssa[2],'b.')
    mp.plot(i, x[0],'r_')
    mp.plot(i, x[1],'b_')
    #mp.plot(i, x[2],'r.')
    mp.show()
    mp.pause(0.0001)



for x, _ in data:
    result = np.dot(x, w)
    print("{}: {} -> {}".format(x[:2], result, unit_step(result)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
