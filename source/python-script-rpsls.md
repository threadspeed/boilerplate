---
title: python script rpsls (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpsls'

Functions in program: 
* `def rpsls(name): `
* `def name_to_number(name):`
* `def number_to_name(number):`

Modules used in program: 
* `import random`

## python rpsls

Python mysql example: rpsls

```python
# Mini Project 1 for An Introduction to Interactive Programming in Python
# Rock-paper-scissors-lizard-Spock template
# urL http://www.codeskulptor.org/#user6-Bb60Bm0lhE99Urb.py

import random

# The key idea of this program is to equate the strings
# "rock", "paper", "scissors", "lizard", "Spock" to numbers
# as follows:
#
# 0 - rock
# 1 - Spock
# 2 - paper
# 3 - lizard
# 4 - scissors

# helper functions

def number_to_name(number):
    # fill in your code below
    if number == 0:
        return "rock"
    elif number == 1:
        return "Spock"
    elif number == 2:
        return "paper"
    elif number == 3:
        return "lizard"
    elif number == 4:
        return "scissors"
    else :
        return None
    # convert number to a name using if/elif/else
    # don't forget to return the result!

    
def name_to_number(name):
    # fill in your code below
    if name == "rock":
        return 0
    elif name == "Spock":
        return 1
    elif name == "paper":
        return 2
    elif name == "lizard":
        return 3
    elif name == "scissors":
        return 4
    else:
        return None
    # convert name to number using if/elif/else
    # don't forget to return the result!


def rpsls(name): 
    # fill in your code below
    print("Player Chooses " + name)
    # convert name to player_number using name_to_number
    player_number = name_to_number(name)
    # compute random guess for comp_number using random.randrange()
    comp_number = random.randrange(0, 4)
    print("Computer Chooses " + number_to_name(comp_number))
    # compute difference of player_number and comp_number modulo five
    win = (player_number - comp_number ) % 5
    # use if/elif/else to determine winner
    # convert comp_number to name using number_to_name
    # print(results)
    if win == 1 or win == 2:
        print("Player wins!\n")
    elif win == 3 or win == 4:
        print("Computer wins!\n")
    elif win == 0:
        print("No one wins!\n")
    else:
        print("Error!")

    
# test your code
rpsls("rock")
rpsls("Spock")
rpsls("paper")
rpsls("lizard")
rpsls("scissors")
#rpsls("fuck")

# always remember to check your completed program against the grading rubric



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
