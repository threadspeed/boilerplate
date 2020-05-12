---
title: python script puzzlegen3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'puzzlegen3'

Functions in program: 
* `def copy(a, b):`
* `def bad_edges(cards, link_count):`
* `def edges(cards, link_count):`
* `def cards(n, t):`

Modules used in program: 
* `import random`
* `import itertools as it`

## python puzzlegen3

Python mysql example: puzzlegen3

```python
#!/usr/bin/env python

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

def bad_edges(cards, link_count):
    e = edges(cards, link_count)
    i = random.randint(0, len(e) - 1)
    return e + [e[i]]

def copy(a, b):
    i = random.randint(0, len(a) - 1)
    b[i] = a[i]
    

if __name__ == '__main__':

    for n in range(2, 1000):
        try:
            t = random.randint(5, 50)
            link_count = random.randint(1, n * t)
            print("Generating deck: ", n, t)
            c = cards(n, t)

            coin = random.randint(0, 1)
            if coin == 0:
                f = edges
            else:
                f = bad_edges
            links = f(c, link_count)

            for i,j in links:
                copy(c[i], c[j])
    
            print("Cards:")
            for i, cc in enumerate(c):
                print(i, cc)

            print("\nLinks:")
            print(links)
            print("**********")
        except ValueError as e:
            print("Unable to generate: ", t, c, link_count, e)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
