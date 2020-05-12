---
title: python script 008 Rock Paper Scissors (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '008 Rock Paper Scissors'

Functions in program: 
* `def _check(a, b):`
* `def _value():`
* `def _ran():`

Modules used in program: 
* `import random`

## python 008 Rock Paper Scissors

Python example: 008 Rock Paper Scissors

```python
# Rock Paper Scissors
# Exercise (and Solution)

# Make a two-player Rock-Paper-Scissors game.
# (Hint: Ask for player plays (using input), compare them, print(out a message of)
# congratulations to the winner, and ask if the players want to start a new game)

# Remember the rules:

# Rock beats scissors
# Scissors beats paper
# Paper beats rock

import random


def _ran():
    com = ["rock", "paper", "scissors"]
    ls = []
    r = random.randint(0, 2)
    for i in com:
        ls.append(i)
    com = ls
    return com[r]


def _value():
    input1 = input("\n\nPLAYER 1: ENTER 'ROCK', 'PAPER', 'SCISSORS'.\n").lower()
    while input1 != "rock" and input1 != "paper" and input1 != "scissors":
        input1 = input("\nWRONG INPUT. Enter again...\n").lower()

    input2 = input("\nPLAYER 2: ENTER ROCK, PAPER, SCISSORS.\n").lower()
    while input2 != "rock" and input2 != "paper" and input2 != "scissors":
        input2 = input("\nWRONG INPUT. Enter again...\n").lower()

    return input1, input2


def _check(a, b):
    input1 = a
    input2 = b
    if (input1 == "rock" and input2 == "scissors") or \
        (input1 == "scissors" and input2 == "paper") or \
        (input1 == "paper" and input2 == "rock"):
        print("\n ************* Player 1 WINS! *************")
    elif (input1 == "paper" and input2 == "paper") or \
        (input1 == "rock" and input2 == "rock") or \
        (input1 == "scissors" and input2 == "scissors"):
        print("\n ************* It's a TIE. *************")
    else:
        if ch == "2":
            print("\n ************* Computer WINS! *************")
        else:
            print("\n ************* Player 2 WINS! *************")


print("\n\n~~~~~~~~~~~~~~~~~~~~~~ \t\tThis is ROCK-PAPER-SCISSORS.\t\t ~~~~~~~~~~~~~~~~~~~~~~\n")
ch = input("Game Mode: \n1. Two Players (Press 1)\n2. Computer (Press 2)\n")
# Two Players
if ch == "1":
    print("\n\tThere are two players in this game.")
    a, b = _value()
    _check(a, b)
    ask = None
    while ask != "no":

        ask = input("\n\nPress any key to start a new game. \"No\" to quit the game.\n").lower()
        if ask != "no":
            print("\n\n\n\t\t\t\tNEW GAME!!")
        else:
            print("THANKS FOR PLAYING! GOOD DAY!")

# Computer
elif ch == "2":
    print("\n\tYou are playing with a computer.")
    ask = None
    while ask != "no":

        a = input("\n\nPLAYER 1: ENTER 'ROCK', 'PAPER', 'SCISSORS'.\n").lower()
        while a != "rock" and a != "paper" and a != "scissors":
            a = input("\nWRONG INPUT. Enter again...\n").lower()
        b = _ran()
        print("\nCOMPUTER: ", b.upper())
        _check(a, b)
        ask = input("\n\n\tPress any key to start a new game. \"No\" to quit the game.\n").lower()
        if ask != "no":
            print("\n\t\t\t\tNEW GAME!!")
        else:
            print("\n\nTHANKS FOR PLAYING! GOOD DAY!")

else:
    print("Wrong Input")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
