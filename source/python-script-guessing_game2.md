---
title: python script guessing game2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game2'

Functions in program: 
* `def already_guessed(guess):`
* `def is_correct(answer, guess):`

Modules used in program: 
* `import random`

## python guessing game2

Python mysql example: guessing game2

```python
import random


count_guesses = 0
answer = random.randint(1, 100)
past_guesses = []


def is_correct(answer, guess):
    return answer == guess


def already_guessed(guess):
    return guess in past_guesses


while True:
    try:
        guess = int(input('Insert your guess between 1 and 100 here'))
        count_guesses += 1
        print(count_guesses)
        if is_correct(answer, guess):
            print("You won the game!")
            break
        elif already_guessed(guess):
            print("You already guessed that number")
        elif count_guesses >= 5:
            print("You have lost due to exceeding the guess limit")
            break
        elif guess > answer:
            print("The number you guessed is too high")
        else:
            print("The number you guessed is too low")
    except ValueError:
        print("That is not a number!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
