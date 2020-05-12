---
title: python script ga str (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ga str'

Functions in program: 
* `def hello_evolver():`

Modules used in program: 
* `import time`
* `import string`
* `import random`

## python ga str

Python example: ga str

```python
import random
import string
import time
from ga_base import Individual, Population

def hello_evolver():

    target = '''Two roads diverged in a yellow wood,
And sorry I could not travel both
And be one traveler, long I stood
And looked down one as far as I could
To where it bent in the undergrowth;

Then took the other, as just as fair,
And having perhaps the better claim,
Because it was grassy and wanted wear;
Though as for that the passing there
Had worn them really about the same,

And both that morning equally lay
In leaves no step had trodden black.
Oh, I kept the first for another day!
Yet knowing how way leads on to way,
I doubted if I should ever come back.

I shall be telling this with a sigh
Somewhere ages and ages hence:
Two roads diverged in a wood, and I
I took the one less traveled by,
And that has made all the difference.'''

    def fitness_func_int(gene):
        fitness = 0
        for i in range(len(gene)):
            fitness += abs(ord(target[i]) - ord(gene[i]))
        return fitness

    def mutation_func_target(offsprings):
        for i in range(len(offsprings)):
            mutation_point = random.randrange(0, offsprings[0].gene_length)
            distance = ord(offsprings[i].gene[mutation_point]) - ord(target[mutation_point])
            while distance == 0:
                mutation_point = random.randrange(0, offsprings[0].gene_length)
                distance = ord(offsprings[i].gene[mutation_point]) - ord(target[mutation_point])

            old_val = ord(offsprings[i].gene[mutation_point])
            if distance > 0:
                offsprings[i].gene[mutation_point] = chr(old_val - 1)
            elif distance < 0:
                offsprings[i].gene[mutation_point] = chr(old_val + 1)
            #print("here ",mutation_point, distance, old_val, ord(offsprings[i].gene[mutation_point]))

        return offsprings

    def mutation_func_blind(offsprings):
        for i in range(len(offsprings)):
            mutation_point = random.randrange(0, offsprings[0].gene_length)
            old_fitness = offsprings[i].fitness

            possible_mutations = random.sample(string.printable, 25)
            mut_index = 0

            can_inc_fitness = old_fitness >= offsprings[i].fitness and offsprings[i].fitness != 0
            while can_inc_fitness and mut_index < len(possible_mutations):
                offsprings[i].gene[mutation_point] = possible_mutations[mut_index]
                mut_index += 1
                offsprings[i].calculate_fitness()

        return offsprings

    def random_func(gene):
        for i in range(len(gene)):
            gene[i] = random.choice(string.printable)
        return gene


    """I now realize that this doesnt matter much,
     since there are only two offsprings every generation."""
    pop_size = 30
    individual_list = []
    for i in range(pop_size):
        individual_list.append(Individual(len(target), 0, fitness_func_int, random_func))

    population = Population(individual_list, mutation_func_target)
    generation_count = 1

    start_time = time.time()

    old_fitness = population.get_fittest().fitness
    while population.get_fittest().fitness != 0:
        fitness_diff_percentage = ((old_fitness - population.get_fittest().fitness)/old_fitness) * 100
        print("Generation:", generation_count,"Least Weakness:",population.get_fittest().fitness," Offspring Improved:",fitness_diff_percentage,"%")
        old_fitness = population.get_fittest().fitness

        #population.get_fittest().printInd("Fittest(Will Reproduce): ")
        #population.get_second_fittest().printInd("Second Fittest: ")
        #population.individuals[-1].printInd("Least Fittest(Killed): ")

        population.crossover()
        population.mutate()
        population.replace_least_fittest()

        generation_count = generation_count + 1

    print("Generations Taken:", generation_count + 1)
    population.get_fittest().printInd("#####Final Fittest")

    elapsed_time = time.time() - start_time
    print(time.strftime("Time Taken: %H:%M:%S", time.gmtime(elapsed_time)))

hello_evolver()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
