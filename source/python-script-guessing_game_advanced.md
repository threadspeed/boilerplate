---
title: python script guessing game advanced (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game advanced'

Functions in program: 
* `def is_close(guess, number):`
* `def is_good_guess(guess):`
* `def is_valid(guess):`
* `def already_guessed(guess):`
* `def is_correct(number, guess):`

Modules used in program: 
* `import random`

## python guessing game advanced

Python example: guessing game advanced

```python
import random
number = int(100 * random.random()) + 1
good_guess_range = [0, 101]
guesses = []


def is_correct(number, guess):
    return number == guess


def already_guessed(guess):
    return guess in guesses


def is_valid(guess):
    try:
        guess = int(guess)
        return guess <= 100 and guess >= 0
    except ValueError:
        return False


def is_good_guess(guess):
    return guess > good_guess_range[0] and guess < good_guess_range[1]


def is_close(guess, number):
    return abs(guess - number) < 6


while True:
    guess = input("Guess a number 1-100: ")
    if not is_valid(guess):
        print("Please enter an integer between 1 and 100")
    else:
        guess = int(guess)
        if already_guessed(guess):
            print("You already guessed that.")
        else:
            guesses.append(guess)
            if is_correct(number, guess):
                print("You win. The number was", number)
                print("Guesses:", len(guesses))
                break
            elif len(guesses) == 5:
                print("Wrong. That was five guesses, you lose.")
                break
            elif not is_good_guess(guess):
                print("That was a pretty dumb guess.")
            else:
                if guess > number:
                    print("Nope. That guess is too high.")
                    good_guess_range[1] = guess
                else:
                    print("That guess is too low.")
                    good_guess_range[0] = guess
                if is_close(guess, number):
                    print("But you're close!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
