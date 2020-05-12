---
title: python script machine-learning linear regression model (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'machine-learning linear regression model'


Modules used in program: 
* `import random`

## python machine-learning linear regression model

Python example: machine-learning linear regression model

```python
from numpy import random as nrandom, zeros
from numpy import matrix
import random

class model:
    def __init__(self):
        self._weight = matrix([])
    @property
    def weight(self):
        return self._weight
    @weight.setter
    def weight(self, value):
        self._weight = value
    def train(self, options):
        data_set = []
        max = 0
        with open(options.train, 'r') as f:
            while True:
                line = f.readline().strip()
                if line:
                    kv = line.split('|')
                    vs = map(lambda x: float(x), kv[1].split(' '))
                    vs.insert(0, 1)
                    if vs.__len__() > max:
                        max = vs.__len__()
                    data_set.append((float(kv[0]), vs))
                else:
                    break
        map(lambda x: x[1] if x[1].__len__() == max else x[1].extend([0 for x in range(0, max - x[1].__len__())]), data_set)
        self.weight = zeros((max, 1))
        for x in range(0, options.passes):
            sub_set = data_set[0: data_set.__len__()]
            features = matrix(map(lambda x: x[1], sub_set))
            real_values = matrix(map(lambda x: [x[0]], sub_set))
            result = features * self.weight
            residuals = result - real_values
            ds = options.learn_rate * (features.transpose() * residuals + options.lreg1 + options.lreg2 * self.weight) / data_set.__len__()
            self.weight = self.weight - ds
            print(residuals)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
