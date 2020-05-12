---
title: python script 07 wizard Game actors (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '07 wizard Game actors'


Modules used in program: 
* `import random`

## python 07 wizard Game actors

Python example: 07 wizard Game actors

```python
import random

class Creature:
    def __init__(self, name, the_level=10):
        self.name = name
        self.level = the_level

    def __repr__(self):
        return('Creature: {} of level {}'.format(
            self.name, self.level
        ))
    def runaway(self):
        pass

    def get_defensive_roll(self):
        return random.randint(1,12)*self.level

class Wizard(Creature):
    def __init__(self, name, level):
        super().__init__(name,level)

    def attack(self, creature):
        print('the wizard {} attacks {}'.format(self.name,creature.name))

        my_roll = random.randint(1,12)*self.level

        creature_roll = creature.get_defensive_roll()
        print('You roll {}'.format(my_roll))
        print('{} rolls {}'.format(creature.name,creature_roll))

        if(my_roll>=creature_roll):
            #print('The Wizard defeated {}'.format(creature.name))
            return True
        else:
            print('Game Over')
            return False

    def lookaround(self, createures):
        print(createures)

    def runaway(self):
        pass


class Dragon(Creature):
    def __init__(self,name, level, scaliness, breath_fire):
        super().__init__(name,level)
        self.scaliness = scaliness
        self.breath_fire=breath_fire

    def get_defensive_roll(self):
        base_roll=super().get_defensive_roll()
        fire_modifier = 5 if self.breath_fire else 1
        scale_modifier=self.scaliness/10
        # if self.breath_fire:
        #     fire_modifier=5
        # else:
        #     fire_modifier=1
        return self.level*scale_modifier*fire_modifier

    def breath_fire():
        pass



class SmallAnimal(Creature):
    def get_defensive_roll(self):
        base_roll = super().get_defensive_roll()
        return base_roll/2


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
