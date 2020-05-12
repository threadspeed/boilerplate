---
title: python script numbergame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'numbergame'

Functions in program: 
* `def top_scores():`
* `def play_game():`
* `def get_score_list():`

Modules used in program: 
* `import random`
* `import json`
* `import datetime`

## python numbergame

Python example: numbergame

```python
import datetime
import json
import random

secret = random.randint(1, 30)
attempts = 0
mode = 0

def get_score_list():
    with open("score_list.txt", "r") as score_file:
        score_list = json.loads(score_file.read())
        return score_list

def play_game():
    secret = random.randint(1, 30)
    mode = input("Please set the difficulty level (easy/hard): ")
    attempts = 0

    with open("score_list.txt", "r") as score_file:
        score_list = json.loads(score_file.read())

    if mode.lower() == "easy":
        while True:
            guess = int(input("Guess the secret number (between 1 and 30): "))
            attempts += 1

            if guess == secret:
                score_list.append({"attempts": attempts, "date": str(datetime.datetime.now())})
                with open("score_list.txt", "r") as score_file:
                    score_list = json.loads(score_file.read())

                print("You've guessed it - congratulations! It's number " + str(secret))
                print("Attempts needed: " + str(attempts))
                break
            elif guess > secret:
                print("Your guess is incorrect... try a lower number.")
            elif guess < secret:
                print("Your guess is incorrectt... try a higher number.")

    elif mode.lower() == "hard":
        while True:
            guess = int(input("Guess the secret number (between 1 and 30): "))
            attempts += 1

            if guess == secret:
                score_list.append({"attempts": attempts, "date": str(datetime.datetime.now())})
                with open("score_list.txt", "r") as score_file:
                    score_list = json.loads(score_file.read())

                print("You've guessed it - congratulations! It's number " + str(secret))
                print("Attempts needed: " + str(attempts))
                break
            elif guess > secret:
                print("INCORRECT")
            elif guess < secret:
                print("INCORRECT")

def top_scores():
    score_list = sorted(get_score_list(), key=lambda k: k['attempts'])
    top_scores = score_list[:5]
    return top_scores


while True:
    selection = input("Would you like to A) play a new game, B) see the best scores, or C) quit?")

    if selection.lower() == "a":
        play_game()
    elif selection.lower() == "b":
        for x in top_scores():
            print(x)
    else:
        break

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
