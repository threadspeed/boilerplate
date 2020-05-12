---
title: python script individual (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'individual'


Modules used in program: 
* `import math`
* `import random as r`

## python individual

Python mysql example: individual

```python
# -*- coding:Utf-8 -*-
import random as r
import math

class Individual:
    def __init__(self, to_guess):
        # Fitness is the number of how far
        # the guess is from the to_guess
        self.fitness = 0
        self.to_guess = to_guess
        self.guess = 0

    def create_guess(self):
        self.guess = math.floor(r.random() * 100)

    def create_fitness(self):
        self.fitness = abs(int(self.to_guess) - self.guess)

    def mutate(self, value):
        self.guess = value


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
