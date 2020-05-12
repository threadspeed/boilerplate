---
title: python script GuessGame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GuessGame'

Functions in program: 
* `def play(difficulty):`
* `def compare_results(difficulty, secret_number):`
* `def get_guess_from_user(difficulty):`
* `def generate_number(difficulty):`

Modules used in program: 
* `import random`

## python GuessGame

Python example: GuessGame

```python
import random


def generate_number(difficulty):
    return random.randint(1, difficulty)


def get_guess_from_user(difficulty):
    user_number = input('guess a number between 1 to ' + str(difficulty))
    if user_number.isnumeric() and 1 <= int(user_number) <= difficulty:
        return user_number
    else:
        print('please enter only number between 1 to ', difficulty)
        get_guess_from_user()


def compare_results(difficulty, secret_number):
    if difficulty == secret_number:
        return True
    return False


def play(difficulty):
    rand_number = int(generate_number(difficulty))
    user_guess = int(get_guess_from_user(difficulty))
    return compare_results(user_guess, rand_number)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
