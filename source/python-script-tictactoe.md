---
title: python script tictactoe (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tictactoe'

Functions in program: 
* `def printBoard():`

Modules used in program: 
* `import random`

## python tictactoe

Python example: tictactoe

```python
# Tic Tac Toe assignmen that my student Grace is working on.
# Saving here until she creates a github account.

# Shruthi & Grace, Make Me Tic-Tac-Toe!

# if you need to use random numbers....
# import random
# randomNumber = random.randint(1, 10)

# To print(text on the screen: print("text goes here"))

# To take in user input call: userInput = raw_input("Your prompt goes here?")

# If you need to convert a string, to an int call something like...
# myString = str(myInteger)
# myInteger = int(myString)

# Python language reference: https://www.w3schools.com/python/default.asp

import random

# Create Game Board
board = ["0", "1", "2", "3", "4", "5", "6", "7", "8"]

# Grace, make me a function which will print(the game board by looking at the)
# board list, and will fill in the spaces appropriatly.
# def printBoard(): ...

def printBoard():
    print(board[0] + " " + board[1] + " " + board[2])
    print(board[3] + " " + board[4] + " " + board[5])
    print(board[6] + " " + board[7] + " " + board[8])


print("         TIC TAC TOE  ")
print("THECODERSCHOOL, FLOWER MOUND TEXAS")
print(" ")
print("The Game Board is Numbered:")
print(" ")
printBoard()
print(" ")
print(" ")
print(" ")

computerSelection = random.randint(1, 9)

print("Computer selects: " + str(computerSelection))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
