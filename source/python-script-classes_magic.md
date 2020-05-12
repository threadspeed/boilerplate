---
title: python script classes magic (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'classes magic'


Modules used in program: 
* `import random`

## python classes magic

Python example: classes magic

```python
import random

class Spell:
    def __init__(self, name, cost, dmg, type):
        self.name = name
        self.cost = cost
        self.dmg = dmg
        self.type = type

    def generate_damage(self):
        low = self.dmg - 15
        high = self.dmg + 15
        return random.randrange(low, high)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
