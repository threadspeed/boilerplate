---
title: python script population (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'population'


Modules used in program: 
* `import math`
* `import random as r`

## python population

Python example: population

```python
# -*- coding:Utf-8 -*-
from individual import *
import random as r
import math

class Population:
    def __init__(self, size):
        self.size = size
        self.pop = []
        self.bests = []
        self.seconds = []
        self.childs = []

    def create_population(self, to_guess):
        self.pop = [Individual(to_guess) for i in range(self.size)]

    def make_guess(self):
        for ind in self.pop:
            ind.create_guess()

    def measure_fitness(self):
        for ind in self.pop:
            ind.create_fitness()

    def selection(self):
        self.pop.sort(key=lambda ind: ind.fitness)
        self.bests = self.pop[0:50]
        self.seconds = self.pop[50:100]

    def get_best(self):
        return self.bests[0].guess

    def random_guess_from_best(self):
        return self.bests[len(self.bests)-1].guess

    def check_for_guess(self, to_guess):
        for ind in self.bests:
            if str(ind.guess) == to_guess:
                return True
        return False

    def mutation(self, mutation_rate):
        for ind in self.seconds:
            if r.random() > mutation_rate:
                ind.mutate(random_guess_from_best())

    def crossover(self, crossover_value):
        for ind in self.bests:
            self.childs.append('s')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
