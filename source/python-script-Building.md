---
title: python script Building (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Building'


Modules used in program: 
* `import random`

## python Building

Python example: Building

```python
import random
class Building:
    def __init__(self, world, name, owner, color, _type):
        self.name = name
        self.owner = owner # Person obj
        self.color = color
        self.type = _type
        
        self.assign_person(owner)

    @property
    def ID(self):
        # unlikely to assign the same ID #
        return random.randrange(100000, 999999)

    def assign_person(self, person):
        person.add_housing(self)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
