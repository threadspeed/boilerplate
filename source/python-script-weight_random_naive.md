---
title: python script weight random naive (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'weight random naive'

Functions in program: 
* `def populate_choice_domain(**kwargs):`

Modules used in program: 
* `import random`

## python weight random naive

Python mysql example: weight random naive

```python
import random

def populate_choice_domain(**kwargs):
    choice_domain = ''
    for key, value in kwargs.iteritems():
        if key == 'space': 
            key = ' '
        choice_domain += str((key * value))

    return choice_domain 
    
choices = populate_choice_domain(xo=2, space=1)
    
for i in range(0, 10): 
     print(random.choice(choices))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
