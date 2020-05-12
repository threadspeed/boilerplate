---
title: python script Live (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Live'

Functions in program: 
* `def game_difficulty():`
* `def get_user_input():`
* `def load_game():`
* `def welcome(name):`

Modules used in program: 
* `import Score`
* `import GuessGame`
* `import MemoryGame`

## python Live

Python example: Live

```python
import MemoryGame
import GuessGame
import Score

def welcome(name):
    return 'Hello ' + name + ' and welcome to the World of Games (WoG).'


def load_game():
    user_input = get_user_input()
    game_diff = game_difficulty()
    if (user_input == 1):
        result = MemoryGame.play(game_diff)
    else:
        result = GuessGame.play(game_diff)
    if result:
        Score.add_score(game_diff)


def get_user_input():
    user_input_game = input(
        '1. Memory Game - a sequence of numbers will appear for 1 second and you have to guess it back \n '
        '2. Guess Game - guess a number and see if you chose like the computer \n')
    if user_input_game.isnumeric() and 1 <= int(user_input_game) <= 2:
        return int(user_input_game)
    else:
        print('please enter only number between 1 to 2')
        get_user_input()


def game_difficulty():
    difficulty = input('Please choose game difficulty from 1 to 5: ')
    if difficulty.isnumeric() and 1 <= int(difficulty) <= 5:
        return int(difficulty)
    else:
        print('please enter only number between 1 to 5')
        game_difficulty()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
