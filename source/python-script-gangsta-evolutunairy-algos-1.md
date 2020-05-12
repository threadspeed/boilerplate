---
title: python script gangsta-evolutunairy-algos-1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gangsta-evolutunairy-algos-1'

Functions in program: 
* `def fitness_test(f, x, optimal_f):`
* `def f(x):`

Modules used in program: 
* `import math`
* `import random`

## python gangsta-evolutunairy-algos-1

Python mysql example: gangsta-evolutunairy-algos-1

```python
import random
import math

def f(x):
    return x**4 + 101*x + 8

optimal_f = 0 #to optimize fuction f
error_allowance = 0.09 #absolute tolerance value
n_species = 100000 #number of iterations
candidate_x = [] # "FIT" species

def fitness_test(f, x, optimal_f):
    f_val = f(x)
    error = math.sqrt((optimal_f - f_val)**2) #rms error
    return error

for i in range(n_species):
    k = round(random.uniform(-100,100), 7)
    error = fitness_test(f, k, optimal_f)
    if error < error_allowance:
        candidate_x.append([error, k])

sorted(candidate_x)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
