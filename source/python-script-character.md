---
title: python script character (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'character'


Modules used in program: 
* `import random`

## python character

Python mysql example: character

```python
import random
from combat import Combat


class Character(Combat):
    level = 1
    attack_limit = 12
    experience = 0
    base_hit_points = 10
    location = (0, 0)

    def attack(self):
        roll = random.randint(1, self.attack_limit)
        if self.weapon == 'Sword':
            roll += 1
        elif self.weapon == 'Axe':
            roll += 2
        return roll > 4

    def get_weapon(self):
        weapon_choice = input('Weapon ([S]word, [A]xe, [B]ow): ').lower()

        if weapon_choice in 'sab':
            if weapon_choice == 's':
                return 'sword'
            elif weapon_choice == 'a':
                return 'axe'
            else:
                return 'bow'
        else:
            return self.get_weapon()

    def __init__(self, **kwargs):
        self.name = input('Name: ')
        self.weapon = self.get_weapon()
        self.hit_points = self.base_hit_points

        for key, value in kwargs.items():
            setattr(self, key, value)

    def __str__(self):
        return '{}, Level {}, HP: {}, XP: {}'.format(self.name, self.level, self.hit_points, self.experience)

    def rest(self):
        if self.hit_points < self.base_hit_points:
            self.hit_points += 1

    def leveled_up(self):
        if self.experience in range(4, 7):
            self.level = 2
            self.attack_limit = 14
            self.base_hit_points = 14
        elif self.experience in range(7, 12):
            self.level = 3
            self.attack_limit = 16
            self.base_hit_points = 16

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
