---
title: python script monster (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'monster'


Modules used in program: 
* `import random`

## python monster

Python mysql example: monster

```python
import random
from combat import Combat

COLORS = ['yellow', 'red', 'blue', 'green', 'black', 'white']


class Monster(Combat):
    min_hit_points = 1
    max_hit_points = 1
    min_experience = 1
    max_experience = 1
    attack_strength = 1
    weapon = 'sword'
    sound = 'roar!'
    location = (0, 0)

    def __init__(self, **kwargs):
        self.hit_points = random.randint(self.min_hit_points, self.max_hit_points)
        self.experience = random.randint(self.min_experience, self.max_experience)
        self.color = random.choice(COLORS)

        for key, value in kwargs.items():
            setattr(self, key, value)

    def __str__(self):
        return '{} {}'.format(self.color.title(),
                              self.__class__.__name__,  # class is Goblin etc. Name is string version.
                              )

    def battlecry(self):
        return self.sound


class Goblin(Monster):  # Goblin is a subclass of Monster, so it just takes attributes from Monster
    max_hit_points = 3
    min_experience = 4
    max_experience = 5
    attack_strength = 3
    sound = 'Squeak!'


class Troll(Monster):
    min_hit_points = 3
    max_hit_points = 6
    min_experience = 4
    max_experience = 6
    attack_strength = 3
    sound = 'Growl!'


class Dragon(Monster):
    min_hit_points = 6
    max_hit_points = 12
    min_experience = 6
    max_experience = 10
    attack_strength = 5
    sound = 'RAAAAAAAAAAAAAARR!!!!!!'

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
