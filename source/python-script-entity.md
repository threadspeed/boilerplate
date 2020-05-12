---
title: python script entity (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'entity'


Modules used in program: 
* `import time`
* `import world`
* `import random`

## python entity

Python example: entity

```python
import random
import world
import time
from file import CustomFile

global entity_id, god_count, creature_count, legendary_creature_count, god_count
legendary_creature_count = 0
god_count = 0

class creature:

    global psychopathy
    global isCreatureLegendary
    global doesCreatureNemesis
    global creature_name_prefix

    creature_name_prefix = ['God']
    master_creature_list = CustomFile.readFileToObj("races.txt")
    master_class_list = CustomFile.readFileToObj("class_names.txt")
    master_generic_name_list = CustomFile.readFileToObj("names.txt")
    assigned_chunk = None

    # some creatures can now spawn psychopathicor with mental disorders.
    ## possibly replace arguments with **kwargs
    def __init__(self, entityid, creatureName, creatureType, creatureClass,
                 creatureLevel, verbose):
        self.name = creatureName
        self.type_ = creatureType
        self.level = creatureLevel
        self.entity_id = entityid
        self.cclass = creatureClass
        isCreatureLegendary = False
        psychopathy = False
        doesCreatureNemesis = False
        # Very random chance to become deity.
        if random.randint(0, 5000) <= 1:
            print('Something very strange is happening...')
            time.sleep(2)
            print('White light swirls around', self.name, '!')
            time.sleep(2)
            self.name = creature_name_prefix[0] + " " + self.name
            print(self.name, 'has become a diety! All hail', self.name, '!')
            time.sleep(2)
            global god_count
            god_count += 1
        if random.randint(0, 100) <= 1:
            # Less than 5 percent chance. Make creature psychopath.
            psychopathy = True
        if random.randint(0, 500) <= 5:
            global legendary_creature_count
            legendary_creature_count += 1
            isCreatureLegendary = True
        if random.randint(0, 500) <= 1:
            doesCreatureNemesis = True
        if verbose:
            if isCreatureLegendary:
                print('Legendary', end=" ")
            print('Creature: ', self.name, 'the', self.cclass, self.type_,
                  'creature, level', self.level, 'has been spawned.')
        if psychopathy and verbose:
            print('\t-> Creature is psychopathic.')
        if doesCreatureNemesis:
            # Creature has claimed a nemesis!
            random_nemesis = world._master_entity_list[random.randrange(
                0, len(world._master_entity_list))]
            print('LOG:\t', self.name, 'has announced', random_nemesis.name,
                  'as their nemesis!')

    def getLegendaryCreatureCount():
        return legendary_creature_count

    def getGodCount():
        return god_count

    def fightEntity(self, entityobj):
        # creature will begin to fight this entity!
        print(self.name, 'will begin to fight', entityobj.name, '!')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
