---
title: python script nn (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nn'

Functions in program: 
* `def test2():`
* `def test1():`

Modules used in program: 
* `import random as rn`
* `import numpy.matrixlib as ml`
* `import random as rn`
* `import numpy as np`

## python nn

Python example: nn

```python
import numpy as np
import random as rn
import numpy.matrixlib as ml
import random as rn
from pprint(import pprint)
from math import *

# vectorized Leaky ReLU and it's derivative
vrelu = np.vectorize(lambda x: x * 0.5 if x >= 0 else 0.1 * x)
vdrelu = np.vectorize(lambda x:  0.5 if x >= 0 else 0.1)

class NN:
    def __init__(self, layers):
        if len(layers) < 2:
            raise ValueError("too few layers")

        # declaring containers
        self.ins = []
        self.outs = []
        self.errs = []
        self.bias = []
        self.wts = []
        self.size = len(layers)
        # iterating over layer sizes in argument
        old = 0
        for i in layers:
            if i < 1:
                raise ValueError("layer dimension is too low")
            self.ins.append(np.zeros((i, 1)))
            self.outs.append(np.zeros((i, 1)))
            self.errs.append(np.zeros((i, 1)))
            # wts[i] connects outs[i] to ins[i+1]
            if(old != 0):
                self.bias.append(np.random.rand(i, 1))
                self.wts.append(np.random.rand(i, old))
            old = i

    def forward(self, l_in):
        self.ins[0] = ml.asmatrix(l_in, dtype=float)
        self.outs[0] = vrelu(self.ins[0])
        for i in range(0, self.size - 1):
            # propagating signal
            self.ins[i + 1] = self.wts[i] * self.outs[i] + self.bias[i]
            self.outs[i + 1] = vrelu(self.ins[i + 1])
        return self.outs[self.size - 1]

    def backward(self, l_act):
        last = self.size - 1
        actual = ml.asmatrix(l_act, float).reshape((len(l_act), 1))
        # calculating error in the last layer
        self.errs[last] = np.multiply(
            self.outs[last] - actual, vdrelu(self.ins[last]))
        # backpropagation
        for i in reversed(range(last)):
            # error in the next layer
            self.errs[i] = np.multiply(
                self.wts[i].T * self.errs[i + 1], vdrelu(self.ins[i]))
            # modifying weights
            self.wts[i] = self.wts[i] - self.errs[i + 1] * self.outs[i].T * 0.6
            # modifying bias
            self.bias[i] = self.bias[i] - self.errs[i + 1] * 0.6
        return self.errs[last]


def test1():
    data = []
    for i in range(1000):
        y = rn.random()
        data.append((y, y / 2))
    pprint(data)

    nn = NN([1, 4, 1])

    for i, o in data:
        r = nn.forward([i])[0][0]
        e = nn.backward([o])[0][0]
        pprint((i, o, r, e))


def test2():
    data = [((x % 10), (x % 10) * x) for x in range(1000)]

    nn = NN([1, 4, 1])

    for i, o in data:
        r = nn.forward([i])[0][0]
        e = nn.backward([o])[0][0]
        pprint((i, o, r, e))


test1()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
