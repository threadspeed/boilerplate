---
title: python script evolutionary-algos-2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'evolutionary-algos-2'

Functions in program: 
* `def fitness_test(f, x, optimal_f):`
* `def quadratic(x):`

Modules used in program: 
* `import math`
* `import random`

## python evolutionary-algos-2

Python example: evolutionary-algos-2

```python
import random
import math

def quadratic(x):
    return x**2 + 7*x + 12 #a simple quadratic function

optimal_val = 0 #to optimize fuction f
error_allowance = 0.01 #absolute tolerance value
n_species = 10000 #number of iterations
possible_x = [] # "FIT" species

def fitness_test(f, x, optimal_f):
    f_val = f(x)
    error = math.sqrt((optimal_f - f_val)**2) #rms error
    return error

for i in range(n_species):
    k = round(random.uniform(-100,100), 5)
    error = fitness_test(quadratic, k, optimal_val)
    if error < error_allowance:
        possible_x.append([error, k])

sorted(possible_x)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
