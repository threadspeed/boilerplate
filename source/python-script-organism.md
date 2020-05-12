---
title: python script organism (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'organism'


Modules used in program: 
* `import copy`
* `import math`
* `import random`

## python organism

Python mysql example: organism

```python
import random
import math
import copy

from chromosome import Nucleotide, Chromosome
from reactor import Reactor
from functools import lru_cache

class Organism(object):
    def __init__(self, parent = None, mutability = 0.1, reactor_size = None, allowed_blocks = None): 
        self.mutability = mutability
        if parent is not None:
            self.chromosome = copy.deepcopy(parent.chromosome)
        else:
            self.chromosome = Chromosome(reactor_size = reactor_size, allowed_blocks = allowed_blocks)

    def __str__(self):
        return str(self.chromosome)

    def evaluate(self):
        r = Reactor(*self.chromosome.reactor_size, self.chromosome.encoded_data())
        return r

    @lru_cache
    def fitness(self):
        return self.evaluate().efficiency

    def mutate(self, amount = None):
        if amount is None:
            amount = self.mutability
        for nucleotide in self.chromosome:
            if random.random() < amount:
                nucleotide.flip(self.chromosome.allowed_blocks)
   
    @property
    def size(self):
        return self.chromosome.x, self.chromosome.z, self.chromosome.height

    @property
    def pretty_size(self):
        return str(self.chromosome.x) + 'x' + str(self.chromosome.z) + 'x' + str(self.chromosome.height)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
