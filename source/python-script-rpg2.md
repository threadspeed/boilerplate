---
title: python script rpg2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpg2'


Modules used in program: 
* `import json`
* `import os`
* `import math`
* `import random`

## python rpg2

Python mysql example: rpg2

```python
#!/usr/bin/python3
# Quando editando com Vi/Vim usar :set tabstop=4 shiftwidth=4 e :set tabexpand problems of indent 
# Code By Wandeson Ricardo
# Blog www.gaenos.blogspot.com

import random
import math
import os
import json

"""
Making game.
Schemematic Prototype. Skell.
We can superclass bellow of the class 'Character

"""
# ----------- Universes -----------------------
# Possible descrition to universes that contain worlds.
# Generic and abstract class
class Universe(object):
    """
        Universes with worlds. Generic class to help create multiple
        virtual ambients for games.
    """
    def __init__(self, **argv):
        self.argv = argv
    def setArgv(self, key, value):
        self.argv[key]= value
    def getArgv(self):
        return self.argv
# --------- Universes super class  ---------------

# Define worlds in game
class World(object):
    #map = [['0','0''0''0''0']
    #           ]
    #map {0: {}}
    def __init__(self, *args):
        self.args =args
        self.mapa = {'Posto':{'Name': 'MiracleX','itens':[]},
                    'Shop':'ShopMax',
                    'Restaurante':'',
                    'Parque':'', 
                    'Floresta':'',
                    'Rua':'',
                    'Casarão':''
        }

    
    
# Superclass. Generic entity. Inanimate.
class Entity(object):
    def __init__(self, pos, *args):
        self.pos = pos
        self.args = args
    def show(self):
        print(self.args)
          
# Base class. Entities live.
class Character(object):
    """
    Base class for buid others classes players, enemies, .
    """
    
    def __init__(self, position, hp, alive=True, size=1):
        self.name = u''
        self.pos = position
        self.hp = hp
        self.alive = alive
        self.size = size
        self.items = {}
    def moveIt(self, new_pos=None):
        self.new_pos = new_pos

        return self.new_pos


    def say(self):
        print('Hi the!')

    def grow(self):
        self.size += 1
        
    # aumenta hp
    def hp_up(self):
        self.hp += 10    
        
# class for items still define better
#class items(Entity):

# Game. Rules and history.
class Game(object):
    def __init__(self):
        self.choice = ''
        self.world = World()    

    def start_game(self):
        print('RPG Adventure\n')
        print("\n\t\t\t\tStart the game\n\n%s\n\n"%str(60*'-'))
        while True:
            print('\nChoices\n\t1. Move\n\t2. Attack\n\t3. Scape \n\t4. Quit')
            self.choice = str(input('Escolha: '))
            if self.choice == 'move':
                print('Move...')
            elif self.choice == 'attack':
                print('Atack')
            elif self.choice == 'scape':
                print('Scape...')
            elif self.choice == 'quit':
                print('Quit game.')
                break
            else:
                print('Command error.(1.move, 2. attack, 3. scape, 4. quit)\n ')
    
    def over(self):
        print("Game Over!")
    def display(self):
        print('\n')

if __name__=="__main__":
    Game = Game()
    Game.start_game()
    Game.over()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
