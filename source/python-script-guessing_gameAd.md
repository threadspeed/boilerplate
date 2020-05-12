---
title: python script guessing gameAd (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing gameAd'

Functions in program: 
* `def user_guess():`
* `def get_random_number():`

Modules used in program: 
* `import random`

## python guessing gameAd

Python mysql example: guessing gameAd

```python
import random

def get_random_number():
    secret_number = random.randrange(1, 100)
    return secret_number

def user_guess():
    guess = int(input("Guess a whole number between 1 and 100: "))
    return guess

secret_number = get_random_number()
top = secret_number + 5
bottom = secret_number - 5
closerange = [bottom, (bottom + 1), (bottom + 2), (bottom +3), (bottom + 4), secret_number, (top - 4), (top - 3), (top - 2), (top - 1), top]

turn = [1, 2, 3, 4, 5]
guesses = []
mini_guesses = []
max_guesses = []

for t in turn:
    guess = user_guess()
    if guess == secret_number:
        print("You win")
        print("You used {} guesses".format(len(guesses) + 1))
        break
    elif guess in guesses:
        print("Ooookkkkaaaayyyy, maybe you should take a break")
        guesses.append(guess)
    elif guess > secret_number:
        print("Too high")
        guesses.append(guess)
        max_guesses.append(guess)
        highest = max(max_guesses)
        highlist = len(max_guesses)
        if guess == highest and highlist > 1:
            print("Don't waste your guesses")
        if guess in closerange:
            print("But you are very close!")
    elif guess < secret_number:
        print("Too low")
        guesses.append(guess)
        mini_guesses.append(guess)
        lowest = min(mini_guesses)
        lowlist = len(mini_guesses)
        if guess == min(mini_guesses) and lowlist > 1:
            print("That was a waste.")
        if guess in closerange:
            print("But you are very close!")


if len(guesses) == 5:
    print("You lose. You used all five guesses. The number was {}".format(secret_number))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
