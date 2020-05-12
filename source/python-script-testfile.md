---
title: python script testfile (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'testfile'


Modules used in program: 
* `import random`

## python testfile

Python mysql example: testfile

```python
import random

# Variables for Stranger Game
game_answer = None
player_answer = None
computer_answer = None
die_roll = None

#Game
game_answer = input('Do you want to play. y or n: ')
if game_answer == 'y'.casefold():
    computer_answer = random.randint(1,6)
    die_roll = random.randint(0,10) # delete this comment and get rid of comment on line 19.
    print('DEBUG: {}'.format(die_roll)) #TODO: Remove after testing
    print("""The stranger says: I choose {}""".format(computer_answer))
    player_answer = int(input('Choose a number: '))
    print("You say 'I choose the number {}'.".format(player_answer))
    print("The stranger smiles slyly. Ready to roll?")
    input('Press any button to continue.')
    #die_roll = random.randint(1,6)
    if computer_answer == player_answer == die_roll:
        print('Looks like it is a draw.')
    elif player_answer == die_roll:
        print('You win, lad. Spot on!')
    elif computer_answer == die_roll:
        print('Another easy win for me. Well played.')
    
  # Original Algorithm - to be added directly after line 26.

elif (die_roll - player_answer) < (die_roll - computer_answer):
        print("""Aye lad, you win. The number was {}, yours was {}, and
mine was {}""".format(die_roll, player_answer, computer_answer))
    elif (die_roll - player_answer) > (die_roll - computer_answer):
        print("""Good game, but you lose lad. The number was {}, yours
was {}, and mine was {}""".format(die_roll, player_answer, computer_answer))

        import random


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
