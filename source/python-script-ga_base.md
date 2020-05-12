---
title: python script ga base (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ga base'


Modules used in program: 
* `import random`
* `import copy`

## python ga base

Python example: ga base

```python
import copy
import random

class Individual:
    """Individual Gene"""
    def __init__(self, gene_length, filler, fitness_func, random_func, rand=True):
        self.gene_length = gene_length
        self.fitness_func = fitness_func
        self.random_func = random_func
        self.filler = filler
        self.gene = [filler] * gene_length
        self.fitness = None

        if rand:
            self.make_random()

        self.calculate_fitness()

    def set_gene(self, gene):
        self.gene = gene
        self.gene_length = len(self.gene)
        self.calculate_fitness()

    def make_random(self):
        self.gene = self.random_func(self.gene)

    def calculate_fitness(self):
        self.fitness = self.fitness_func(self.gene)

    def printInd(self, s=""):
        print(s,"[Weakness:",self.fitness,"]\n", "".join(self.gene))


class Population:
    """Collection of genes"""
    def __init__(self, individuals, mutation_func):
        self.individuals = individuals
        self.mutation_func = mutation_func
        self.fitness_check()
        self.population_size = len(individuals)
        self.offsprings = []

    def get_fittest(self):
        return self.individuals[0]

    def get_second_fittest(self):
        return self.individuals[1]

    def fitness_check(self):
        self.individuals = sorted(self.individuals, key=lambda x: x.fitness)

    def crossover(self):
        fittest_parent_0 = self.get_fittest()
        fittest_parent_1 = self.get_second_fittest()

        #fittest_parent_0.printInd("0BC")
        #fittest_parent_1.printInd("1BC")

        #swap here
        self.offsprings = [copy.deepcopy(fittest_parent_0), copy.deepcopy(fittest_parent_0)]

        crossover_point = random.randrange(0, fittest_parent_1.gene_length)
        for i in range(crossover_point, fittest_parent_1.gene_length):
            self.offsprings[0].gene[i] = fittest_parent_1.gene[i]

        for i in range(0, crossover_point):
            self.offsprings[1].gene[i] = fittest_parent_1.gene[i]

        self.offsprings[0].calculate_fitness()
        self.offsprings[1].calculate_fitness()

        #self.offsprings[0].printInd("0AC")
        #self.offsprings[1].printInd("1AC")


    def mutate(self):
        #self.offsprings[0].printInd("0B")
        #self.offsprings[1].printInd("1B")

        self.offsprings = self.mutation_func(self.offsprings)
        self.offsprings[0].calculate_fitness()
        self.offsprings[1].calculate_fitness()

        #self.offsprings[0].printInd("0A")
        #self.offsprings[1].printInd("1A")

    def replace_least_fittest(self):
        self.offsprings = sorted(self.offsprings, key=lambda x: x.fitness)

        self.individuals[-1] = self.offsprings[0]
        self.individuals[-2] = self.offsprings[1]
        self.fitness_check()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
