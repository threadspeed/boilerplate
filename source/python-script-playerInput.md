---
title: python script playerInput (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'playerInput'

Functions in program: 
* `def parsePlayerInput(plinput):`
* `def clearScreen():`
* `def primitivePlayerInput():`
* `def passPlayerObject(object):`

Modules used in program: 
* `import os`
* `import world`

## python playerInput

Python example: playerInput

```python
import world
import os
from player import Player

# We need to pass the specific player object instance to this input class.
def passPlayerObject(object):
    global passed_player_object
    passed_player_object = object


def primitivePlayerInput():
    playerInput = input("> ")
    parsePlayerInput(playerInput)


def clearScreen():
    print('\n' * 100)


def parsePlayerInput(plinput):

    # all used commands must be put into this list to check later.
    approved_commands = [
        "region_count", "list_creature_regions", "simulate_history", "select",
        "!", "clear", "cls", "help", "list_creature_details", "inventory"
    ]
    # let's try something with multiple words.
    split_plinput = plinput.split()
    # fix case sensitivty
    # saving the old variable.
    pre_lower = plinput
    plinput = plinput.lower()
    ##
    # Start attempting to parse input.
    ##
    if split_plinput[0] == "select":
        if len(split_plinput) > 1:
            # if theres something more than just the first world
            # "If you select something, what do you want to do with it?"
            # if split_plinput[1] is type(creature):
            return
    # help
    if plinput == "help": print(", ".join(approved_commands))
    # clear / cls, just push the screen up.
    if plinput == "clear" or plinput == "cls": clearScreen()
    # substring variable manipulation?
    if plinput[:1] == "!":
        temp_string = pre_lower[1:]
        # !giveLevel - Gives player one level.
        if temp_string == "giveLevel": 
            passed_player_object.playerLevel += 1
            print(passed_player_object.playerName, 'has gained 1 level.')
            print(passed_player_object.playerName, 'is now level', passed_player_object.playerLevel)
        # !changePlayerName - Changes the players name.
        elif temp_string == "changePlayerName":
            passed_player_object.playerName = input('What would you like your new name to be?')
            print('Light shines down from above. You feel like a new person. You are now', passed_player_object.playerName)
        else:
            print(
                'The debug cmd does not currently exist. Remember, debug cmds are case sensitive.'
            )
    # now we're going to try to use some stuff.
    if split_plinput[0] == "use":
        # if split_plinput[1] is in passed_player_object.inventory:
        if split_plinput[1] in range(2):
            if split_plinput[1] == '1':
                print('You drink the Elixer of Life.')
            else:
                print('You cannot use that item.')
    # list_creature_details - Lists all creatures that have currently been generated in the world and lists their: name, level, type, and class.
    if plinput == "inventory":
        # Start to display inventory stuff.
        # should we clear the screen?
        # clearScreen()
        print('You open up your Bag of Holding...')
        print('|[ 1. Elixer of Life ]|', 'Drinking this potion gives the player 25 life points back instantly.')
        print('|[ 2. Scroll of Protection ]|', 'Using an action to read the scroll encloses you in a invisible barrier that extends from you to form a 5-foot-radius, 10-foot-high cylinder.')

    if plinput == "list_creature_details":
        for creatureobj in world._master_entity_list:
            print(creatureobj.name, 'the level', creatureobj.level, creatureobj.type_, creatureobj.cclass)
    if plinput == "region_count":
        print(world._chunks_population)
    if plinput == "list_creature_regions":
        for creatureobj in world._master_entity_list:
            print(creatureobj.name, '[' + str(creatureobj.entity_id) + ']',
                  'is located in', creatureobj.assigned_chunk.chunk_name)
    if plinput == "simulate_history":
        world.__simulateHistory(True)

    # If command does not exist.
    if plinput not in approved_commands:
        if split_plinput[0] not in approved_commands:
            if plinput[:1] not in approved_commands:
                print('Incorrect command.')
    # We exit the function by recursion.
    primitivePlayerInput()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
