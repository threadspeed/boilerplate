---
title: python script Homework 5-2 levels (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Homework 5-2 levels'

Functions in program: 
* `def goodbye_message():`
* `def sorted_top_scores():`
* `def play_game(level):`

Modules used in program: 
* `import datetime`
* `import json`
* `import random`

## python Homework 5-2 levels

Python mysql example: Homework 5-2 levels

```python
import random
import json
import datetime


def play_game(level):
    secret = random.randint(1, 30)
    attempts = 0
    wrong_guesses = []
    players_name = str(input("What is your name? Type here:"))
    while True:
        guess = int(input("Guess the secret number (between 1 and 30): "))
        attempts += 1

        if guess == secret:
            with open("score_list_functions.txt", "r") as score_file:
                score_list_functions = json.loads(score_file.read())
            print("You've guessed it - congratulations! It's number " + str(secret))
            print("Attempts needed: " + str(attempts))
            current_time = datetime.datetime.now()
            current_time = current_time.strftime("%d.%m.%Y, %H:%M:%S")
            score_list_functions.append({"player": players_name, "attempts": attempts, "date": str(current_time),
                                         "wrong guesses": wrong_guesses, "secret number": str(secret)})
            with open("score_list_functions.txt", "w") as score_file:
                score_file.write(json.dumps(score_list_functions))
            break

        elif guess > secret:
            wrong_guesses.append(guess)
            if level == "easy":
                print("Your guess is not correct... try something smaller")

        elif guess < secret:
            wrong_guesses.append(guess)
            if level == "easy":
                print("Your guess is not correct... try something bigger")


def sorted_top_scores():
    with open("score_list_functions.txt", "r") as score_file:
        score_list_functions = json.loads(score_file.read())
        sorted_scores_list = sorted(score_list_functions, key=lambda k: k['attempts'])

        for score_dict in sorted_scores_list[:3]:
            print(
                "Name: " + score_dict["player"] + ", " + "wrong guesses: " + str(score_dict.get("wrong guesses")) + ", "
                + str(score_dict["attempts"]) + " attempts, " + "secret number was "
                + str(score_dict.get("secret number")) + ", date: " + score_dict.get("date"))


def goodbye_message():
    print("Thanks for playing! Bye!")


while True:
    selection = input("Would you like to A) play a new game, B) see the best scores, or C) quit?")

    if selection == "A":
        level = input("Choose 'easy' or 'hard' mode!")
        play_game(level)
    elif selection == "B":
        sorted_top_scores()
    else:
        goodbye_message()
        break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
