---
title: python script guessing game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game'

Functions in program: 
* `def number_gen():`
* `def guest_input():`

Modules used in program: 
* `import random`

## python guessing game

Python mysql example: guessing game

```python
#pick a random number between 1 and 100 and repeatedly ask you for guesses.
import random

#have at least two functions.

def guest_input():
    return int(input("Guess a number between 1 and 100 "))

def number_gen():
    return random.randint(1, 100)

user_guess_list = []
rand_num = number_gen()
count = 5 #output the number of turns taken

while count > 0:
    user_guess = guest_input()
    if user_guess in user_guess_list:
        print("I guess you weren't burdened with an overabundance of schooling.")
        continue #if same answer is given, be snarky.

    user_guess_list.append(user_guess)

    if user_guess == rand_num:
        print("You win! It took you {} guesses".format(len(user_guess_list))) #if guess is correct, tell user they win and end game.
        break
    elif count == 1:
        print("Game over, you lose!") #after 5 incorrect guesses, tell user they lost game
        break
    elif user_guess > rand_num:
        print("Guess was too high ") #if guess is too high, tell guess was too high.
        count -= 1
    elif user_guess < rand_num:
        print("Guess was too low ") #if guess is too low, tell guess was too low.
        count -= 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
