---
title: python script 07 wizard Game program (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '07 wizard Game program'

Functions in program: 
* `def game_loop():`
* `def print_header():`
* `def main():`

Modules used in program: 
* `import random`

## python 07 wizard Game program

Python example: 07 wizard Game program

```python
import random

from actors import Wizard, Creature, SmallAnimal, Dragon


def main():
    print_header()
    game_loop()

def print_header():
    print('----------------------------')
    print('--------GAME_WIZARD---------')
    print('----------------------------')

def game_loop():

    createures = [
        SmallAnimal('Toad',1),
        Creature('Tiger',15),
        SmallAnimal('Bat',3),
        Dragon('Dragon',50,75,True),
        Wizard('Evil Wizard',1000)

    ]

    hero =Wizard('Gandalf',75)

    print(createures)

    while True:
        active_creature=random.choice(createures)
        print('A {} has appeared at level {}'.format(active_creature.name,active_creature.level))
        cmd = input('do you [a]ttack [r]unaway or [l]ookaround? ')
        if cmd =='a':
            if hero.attack(active_creature):
                createures.remove(active_creature)
            else: break

        elif cmd =='r':
            hero.runaway()
        elif cmd =='l':
            hero.lookaround(createures)
        else:
            print('OK exiting game')
            break

        if not createures:
            print('you have defeated all creatures, well done')
            break


if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
