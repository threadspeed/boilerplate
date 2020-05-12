---
title: python script Perceptron%2520Model%2520%2520-%2520XOR%2520Gate%2520(Graphical) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Perceptron%2520Model%2520%2520-%2520XOR%2520Gate%2520(Graphical)'


Modules used in program: 
* `import random`
* `import numpy as np`
* `import matplotlib.pyplot as mp`

## python Perceptron%2520Model%2520%2520-%2520XOR%2520Gate%2520(Graphical)

Python mysql example: Perceptron%2520Model%2520%2520-%2520XOR%2520Gate%2520(Graphical)

```python
#! python3
import matplotlib.pyplot as mp
import numpy as np
import random
mp.ion()
fig=mp.figure()
mp.axis([0,100,-1,2])
data = [
    (np.array([0,0,1]), 0),
    (np.array([1,0,1]), 1),
    (np.array([0,1,1]), 1),
    (np.array([1,1,1]), 0),
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
    mp.subplot(3, 1, 1)
    mp.subplots_adjust(left=0.125, bottom=0.1, right=0.9, top=0.9, wspace=0.2, hspace=0.3)
    mp.ylabel('Error Values')
    mp.plot(i, error,'m.')
    mp.subplot(3, 1, 2)
    mp.subplots_adjust(left=0.125, bottom=0.1, right=0.9, top=0.9, wspace=0.2, hspace=0.3)
    mp.plot(i, ssa[0],'r.')
    mp.plot(i, ssa[1],'b.')
    mp.plot(i, ssa[2],'g.')
    mp.ylabel('Change in Weights')
    mp.subplot(3, 1, 3)
    mp.subplots_adjust(left=0.125, bottom=0.1, right=0.9, top=0.9, wspace=0.2, hspace=0.3)
    mp.plot(i, x[0],'r.')
    mp.plot(i, x[1],'b_')
    #mp.plot(i, x[2],'g.')
    mp.ylabel(' X-Values')
    mp.show()
    mp.pause(0.0001)

while True:
    mp.pause(0.0001)

for x, _ in data:
    result = np.dot(x, w)
    print("{}: {} -> {}".format(x[:2], result, unit_step(result)))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
