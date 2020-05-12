---
title: python script guess number (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess number'

Functions in program: 
* `def get_input(guess):`
* `def range1000():`
* `def range100():`

Modules used in program: 
* `import simplegui`
* `import random`

## python guess number

Python mysql example: guess number

```python
# Mini Project 2 for An Introduction to Interactive Programming in Python
# template for "Guess the number" mini-project
# input will come from buttons and an input field
# all output for the game will be printed in the console
# url http://www.codeskulptor.org/#user6-irmTc4hgQqb60Du.py

import random
import simplegui

# initialize global variables used in your code
n = 0
i = 0

# define event handlers for control panel
    
def range100():
    # button that changes range to range [0,100) and restarts
    global n
    global i
    n = random.randrange(0,100)
    #print('n=',n)
    i = 6
    
def range1000():
    # button that changes range to range [0,1000) and restarts
    global n
    global i
    n = random.randrange(0,1000)
    #print('n=',n)
    i = 7
    
def get_input(guess):
    # main game logic goes here	
    guess = int(guess)
    print('guess =', guess)
    global n,i
    #print('n=',n)
    print('i=',i)
    if i>0:
        i -= 1
        if guess == n:
            print('Correct!')
        elif guess < n:
            print('Higher. You have guesses.', i)
        else:
            print('Lower. You have guesses.', )
    else:
        print('You have no guesses.')

    
# create frame
frame = simplegui.create_frame('guess', 300,200)

# register event handlers for control elements
frame.add_button('range 0-100', range100)
frame.add_button('range 0-1000', range1000)
frame.add_input('Guess', get_input, 50)

# start frame
frame.start()

# always remember to check your completed program against the grading rubric

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
