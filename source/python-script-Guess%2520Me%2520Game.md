---
title: python script Guess%2520Me%2520Game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Guess%2520Me%2520Game'


Modules used in program: 
* `import random`

## python Guess%2520Me%2520Game

Python example: Guess%2520Me%2520Game

```python
# -*- coding: utf-8 -*-
#%%
import random
a = random.randint(1, 6)
guess = 0

while a != guess:  
    guess = input("What's your guess?")
    
    if guess == "exit":
        print(("If your quitting something this easy, you'll have a nice time at mc donald's"))
        break 

    guess = int(guess)
    if a > guess:
        print(("Too little, try again"))
    if a < guess:
        print(("Too high, get your head out of the clouds, retry"))

if a == guess:
    print("Good Job! You Guessed Right!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
