---
title: python script puzzlegen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'puzzlegen'

Functions in program: 
* `def copy(a, b):`
* `def edges(cards, link_count):`
* `def cards(n, t):`

Modules used in program: 
* `import random`
* `import itertools as it`

## python puzzlegen

Python example: puzzlegen

```python
import itertools as it
import random

def cards(n, t):
    nt = n*t
    images = range(nt)
    return [[j for j in images[i:i + t]] for i in range(0, n*t, t)]

def edges(cards, link_count):
    ct = min(len(cards), link_count) # we can't have more edges than cards for prop4
    pairs = it.combinations(range(len(cards)), 2)
    population = list(pairs)
    return random.sample(population, ct)

def copy(a, b):
    i = random.randint(0, len(a) - 1)
    b[i] = a[i]
    
c = cards(7, 10)
edges = edges(c, 3)

for i,j in edges:
    copy(c[i], c[j])
    
for i, cc in enumerate(c):
    print(i, cc)
print("")
print(edges)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
