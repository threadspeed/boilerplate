---
title: python script rpg statistics (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpg statistics'


## python rpg statistics

Python mysql example: rpg statistics

```python
"""
This is the basic class for all the living beings, meaning all other characters will become a
child from this parent
"""


class Character:
    """
    This is the base value for all characters, do not change!
    """

    base_name = ""
    base_health = 0
    base_damage = 0
    base_energy = 0
    base_defence = 0
    base_evade = 0
    base_level = 0
    base_exp = 0
    dead = False
    weapon_equipped = False
    armour_equipped = False

    def __init__(self, **kwargs):
        self.health = kwargs["health"]
        self.name = kwargs["name"]
        self.energy = kwargs["energy"]

        if "health" in kwargs:
            self.health = kwargs["health"]
        else:
            self.health = self.base_health #+ 10

        if "energy" in kwargs:
            self.energy = kwargs["energy"]
        else:
            self.energy = self.base_energy #+ 5

        if "abilities" in kwargs:
            self.abilities = kwargs["abilities"]
        else:
            self.abilities = kwargs[""]

        if 'level' in kwargs:
            self.level = kwargs['level']
        else:
            self.level = self.base_level

        if 'xp' in kwargs:
            self.xp = kwargs['xp']
        else:
            self.xp = self.base_exp

        if 'damage' in kwargs:
            self.damage = kwargs['damage']
        else:
            self.damage = self.base_damage #+ 1

        if 'defence' in kwargs:
            self.defence = kwargs['defence']
        else:
            self.defence = self.base_defence

        if 'evade' in kwargs:
            self.evade = kwargs['evade']
        else:
            self.evade = self.base_evade #+ 10

    """
    character values:
    
    """

    name = ""
    level = 0
    exp = 0
    health = 10
    energy = 5
    damage = 1
    evade = 5
    defence = 0

    max_health = base_health + (level * 3 + 1)
    dead = False
    max_energy = base_energy + (level * 1.5)

    abnormal_stats = {
        "poisoned": False,
        "cursed": False,
        "ignited": False,
        "stunned": False
    }

    position = {
        "x": 0,
        "y": 0,
        "z": 0
    }

    level_scale = {
        1: range(0, 10),
        2: range(11 - 20),
        3: range(21 - 30),
        4: range(31 - 40),
        5: range(41 - 50)
    }

    """
    the definition of actions, maybe not have here. Move to child <player> class.
    
    """

    def get_health(self):
        return self.health

    def set_health(self, health):
        if type(health) == int:
            self.health += health
            if self.health <= 0:
                self.dead = True

    def get_energy(self):
        return self.energy

    def set_energy(self, energy):
        if type(energy) == int:
            self.energy += energy

    def take_damage(self, amount):
        self.health = self.health - amount

    def heal_damage(self, amount):
        self.health = self.health + amount

    def learn_ability(self, ability):
        self.abilities[ability.name] = ability

    def get_ability(self):
        return self.abilities.keys()

    def use_ability_self(self, name):
        self.abilities[name].use(self)

    def use_ability_target(self, name, target):
        self.abilities[name].use(target)

    def get_level(self):
        return self.level

    def get_name(self):
        return self.name

    def level_up(self):
        self.level = + 1
        self.max_health = int((self.level * 1.2) * self.base_health)
        self.max_energy = int((self.level * 1.2) * self.base_energy)

    def get_exp(self):
        return self.exp

    def set_exp(self, exp):
        if type(exp) == int:
            self.exp += exp
            for i in self.level_scale:
                if self.level < i and self.exp in self.level_scale[i]:
                    self.level_up()

    def get_position(self):
        return self.position

    def set_position(self, **kwargs):
        if 'x' in kwargs:
            self.position['x'] = kwargs['x']
        if 'y' in kwargs:
            self.position['y'] = kwargs['y']
        if 'z' in kwargs:
            self.position['z'] = kwargs['z']

    def player_status(self):
        return """
    Name:   {}
    Level:  {}
    XP:     {}
    HP:     {}
    MP:     {}
    DMG:    {}
    EV:     {}
    DF:     {}
            """.format(self.name,
                       self.level,
                       self.exp,
                       self.health,
                       self.energy,
                       self.damage,
                       self.evade,
                       self.defence)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
