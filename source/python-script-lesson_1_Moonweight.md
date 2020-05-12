---
title: python script lesson 1 Moonweight (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lesson 1 Moonweight'

Functions in program: 
* `def moon_weight_2():`
* `def moon_weight(weight, mass, year ):`

Modules used in program: 
* `import sys`
* `import dateutil.relativedelta`
* `import sys`

## python lesson 1 Moonweight

Python mysql example: lesson 1 Moonweight

```python
import sys
import dateutil.relativedelta
#weight = 75
#for year in range (1, 16):
#    weight1 = (weight + 1)
#    weight2 = weight1 * 0.165
#    weight = weight + 1
#    print('Год %s  вес = %s' % (year, weight2))

def moon_weight(weight, mass, year ):
    for year in range (year):
        weight1 = (weight + 1)
        weight2 = weight1 * mass
        weight = weight + 1
        print('Год %s  вес = %s' % (year, weight2))

moon_weight(100, 0.28, 5)

import sys

def moon_weight_2():
    print('Введите ваш нынешный земной вес')
    weight = int(sys.stdin.readline())
    print('На сколько килограммов будете полнеть на спутнике ?')
    grow = int(sys.stdin.readline())
    print('Сколько лет Вы планируете пробыть на луне ?')
    year = int(sys.stdin.readline())
    for year in range (1, year + 1):
        grow_up = grow
        weight2 = (weight + grow_up) * 0.165
        weight = weight + 1
        print('Год %s  вес = %s' % (year, weight2))


moon_weight_2()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
