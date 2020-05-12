---
title: python script homework2norm (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'homework2norm'

Functions in program: 
* `def player_choice():`

Modules used in program: 
* `import random`

## python homework2norm

Python example: homework2norm

```python
import random

answer = random.randint(1, 100)

def player_choice():
    num_of_tries = 5
    guesses = []
    while num_of_tries >= 0:
        print("-" * 15)
        print("You have {} tries left to guess my number.".format(num_of_tries))
        guess = input("Guess a number between 1 and 100. ")
        try:
            int(guess)
        except ValueError:
            print("You did not enter a valid number. Guess again.")
            continue
        if int(guess) == answer:
            print("You guessed my number, you win!")
            break
        elif guess in guesses:
            print("You already guessed that... Are you okay?")
            continue
        elif int(guess) < answer:
            print("Your guess was too low. Guess again.")
        elif int(guess) > answer:
            print("Your guess was too high. Guess again.")

        num_of_tries -= 1

        if num_of_tries == 0:
            print("You did not guess my number. Better luck next time!")
            break

        guesses.append(guess)


player_choice()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
