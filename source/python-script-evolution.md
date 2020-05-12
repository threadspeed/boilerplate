---
title: python script evolution (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'evolution'

Functions in program: 
* `def go(goal):`
* `def mutate(string):`
* `def evolve(start, goal):`
* `def judge_fitness(phrase, goal):`
* `def random_string(length):`
* `def random_letter():`

Modules used in program: 
* `import random`

## python evolution

Python example: evolution

```python
# idea from first paragraph: http://www.sciam.com/article.cfm?id=15-answers-to-creationist&page=4
 
import random
 
characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234569890,.-()[]'?\"/!:=\\ "
 
def random_letter():
  return characters[random.randint(0,len(characters)-1)]
 
def random_string(length):
  return ''.join([random_letter() for i in range(length)])
 
def judge_fitness(phrase, goal):
  fitness = 0
  for i in range(len(goal)):
    if phrase[i] == goal[i]:
      fitness += 1
  return float(fitness)/float(len(goal))
 
def evolve(start, goal):
  current_species = start
  current_fitness = judge_fitness(start, goal)
  while current_fitness < 1:
    while True:
      mutated = mutate(current_species)
      mutated_fitness = judge_fitness(mutated, goal)
      if mutated_fitness > current_fitness:
        print('*** %s (%f)' % (mutated, mutated_fitness))
        break
    current_species = mutated
    current_fitness = judge_fitness(current_species, goal)
  print('Done!')
 
def mutate(string):
  a = [c for c in string]
  a[random.randint(0,len(a)-1)] = random_letter()
  return ''.join(a)
 
def go(goal):
  start = random_string(len(goal))
  print('starting with "%s"' % start)
  try:
    evolve(start, goal)
  except KeyboardInterrupt:
    print
 
if __name__ == '__main__':
  try:
    while 1:
      go(raw_input('Goal: '))
  except KeyboardInterrupt:
    print


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
