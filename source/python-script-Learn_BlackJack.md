---
title: python script Learn BlackJack (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Learn BlackJack'


Modules used in program: 
* `import types`
* `import random`

## python Learn BlackJack

Python example: Learn BlackJack

```python
import random
import types

class Player(object):

    def __init__(self, name, amount = 100):
        self.name = name
        self.amount = amount

    def __add__(self, other):
        self.amount += other

    def __radd__(self, other):
        pass

    def __str__(self):
        return self.name + ": " + str(self.amount)

a = Player("Prashanth", 100)
print(a)
a = a + 10



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
