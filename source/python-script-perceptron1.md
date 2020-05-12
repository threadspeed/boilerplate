---
title: python script perceptron1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'perceptron1'


Modules used in program: 
* `import random`
* `import numpy as np`

## python perceptron1

Python mysql example: perceptron1

```python
import numpy as np
import random

class Perceptron:
	def __init__(self):
		self.errors = []
		self.w = np.random.rand(3) 
		
	def train(self, X, alpha, num_iters):
		self.training_data = X
		for i in xrange(num_iters): 
		    x, expected = random.choice(self.training_data) 
		    result = np.dot(self.w, x) 
		    error = expected - self.unit_step(result) 
		    self.errors.append(error) 
		    self.w += alpha * error * x 

	def unit_step(self, val):
		return 0 if val < 0 else 1 

	def test(self):
		for x, _ in self.training_data: 
		    val = np.dot(x, self.w) 
		    print("{}: {} -> {}".format(x[:2], val, self.unit_step(val)))



training_data = [ (np.array([0,0,1]), 0), (np.array([0,1,1]), 1), (np.array([1,0,1]), 1), (np.array([1,1,1]), 1), ] 
p = Perceptron()
p.train(training_data, 0.2, 100)
p.test()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
