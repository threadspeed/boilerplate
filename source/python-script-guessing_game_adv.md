---
title: python script guessing game adv (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game adv'

Functions in program: 
* `def guess_close():`
* `def too_high():`
* `def too_low():`
* `def number_gen():`
* `def guest_input():`

Modules used in program: 
* `import random`

## python guessing game adv

Python example: guessing game adv

```python
#pick a random number between 1 and 100 and repeatedly ask you for guesses.
import random
#have at least two functions.

def guest_input():
    try:    
        return int(input("Guess a number between 1 and 100 "))
    except ValueError:
        print("That's not a number!")

def number_gen():
    return random.randrange(1, 100)

def too_low():
    if len(user_guess_list) < 0 and user_guess < min(user_guess_list):
        print("That response is far too low")

def too_high():
    if len(user_guess_list) < 0 and user_guess > max(user_guess_list):
        print("That answer is WAYY too high!!")

def guess_close():
    if abs((user_guess - rand_num) <= 10):
        print("You're close, at least within 10!")


user_guess_list = []
rand_num = number_gen()
count = 5 #output the number of turns taken


while count > 0:
    user_guess = guest_input()
    print(rand_num)
    if user_guess in user_guess_list:
        print("I guess you weren't burdened with an overabundance of schooling.")
        continue #if same answer is given, be snarky.
    elif user_guess == rand_num:
        print("You win! It took you {} guesses".format(len(user_guess_list))) #if guess is correct, tell user they win and end game.
        exit()
    elif len(user_guess_list) < 0 and user_guess < min(user_guess_list):
        print("That response is farr too low")
    elif len(user_guess_list) < 0 and user_guess > max(user_guess_list):
        print("That answer is way too high!")
    elif abs(user_guess - rand_num) <= 10:
        print("You're close, at least within 10!")

    user_guess_list.append(user_guess)

    if count == 1:
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
