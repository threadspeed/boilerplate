---
title: python script perceptron (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'perceptron'


Modules used in program: 
* `import random`
* `import numpy as np`

## python perceptron

Python example: perceptron

```python
import numpy as np
import random

unit_step = lambda x: 0 if x < 0 else 1 

## create dummy data
training_data = [ (np.array([0,0,1]), 0), (np.array([0,1,1]), 1), (np.array([1,0,1]), 1), (np.array([1,1,1]), 1), ] 
w = np.random.rand(3) 
errors = [] 
learning_rate = 0.2 
n = 100 

for i in xrange(n): 
    x, expected = random.choice(training_data) 
    result = np.dot(w, x) 
    error = expected - unit_step(result) 
    errors.append(error) 
    w += learning_rate * error * x 

for x, _ in training_data: 
    result = np.dot(x, w) 
    print("{}: {} -> {}".format(x[:2], result, unit_step(result)))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
