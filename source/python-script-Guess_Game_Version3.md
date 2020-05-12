---
title: python script Guess Game Version3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Guess Game Version3'

Functions in program: 
* `def crypt(string):`
* `def random_pick(hardness):`
* `def pick_random_split(table):`
* `def select_diff(level, times):`

Modules used in program: 
* `import string`
* `import random`

## python Guess Game Version3

Python mysql example: Guess Game Version3

```python
import random
import string
from math import*

yes = True
no = False
response = True
score = 0
words = ["python",
         "hiking",
         "forest",
         "sea",
         "stockholm",
         "aircraft",
         "break",
         "foundation"
        ]

list2 = []
# select the level the user will play in


def select_diff(level, times):
    limit = 5
    hardness = 1
    if level == 1:
        limit = 5
        if not times:
            print(f"< you have {limit} tries >")
    elif level == 2:
        limit -= 2
        hardness += 2
        if not times:
            print(f"< you have {limit} tries >")
    elif level == 3:
        limit -= 4
        hardness += 4
        if not times:
            print(f"< you have {limit} try >")
    return limit and hardness

# choose a word randomly from 'words' and split it into two strings


def pick_random_split(table):
    phrase = random.choice(table)
    a = phrase[0:ceil((len(phrase)/2))]
    b = phrase[ceil((len(phrase)/2)):]
    st = a + " " + b
    return st

# This function picks random letters


def random_pick(hardness):
    import random
    letters = ''.join([random.choice(string.ascii_letters)
                      for n in range(hardness)])
    ch = ""
    for letter in letters:
        if letter not in "0123456789":
            ch += letter
    return ch

# Crypting the final string by appending each letter to a list, shuffling the list
# and glue every item to form a string "the one the user will see"


def crypt(string):
    for letter in string:
        list2.append(letter)
    random.shuffle(list2)
    glued = ""
    for item in list2:
        glued += item + " "
    list2.clear()
    return glued


# A while loop, in it the main program


while True:
    level = input("  # Welcome to my Guessing Game :)\n"
                  "Which difficulty level\n"
                  "do you wanna play on ?\n"
                  "(1) Easy\n"
                  "(2) Medium\n"
                  "(3) Hard\n"
                  "=> Press 'help' for help\n"
                  "> ")
    if level.upper() == 'HELP':
        print("just choose (1), (2) or (3) for a level <:)")
        try:
            level = int(input("> "))
        except ValueError:
            print("you just entered 'help' !\nnow you have 5 tries\nyou can change difficulty level later")
    else:
        if level in "0123456789":
            level = int(level)
    # select_diff(level)
    a_b = pick_random_split(words)
    list1 = a_b.split(" ")
    times = True
    diff = select_diff(level, times)
    before_crypt_string_guess = list1[0] + random_pick(diff) + list1[1]
    list1.clear()
    final_string = crypt(before_crypt_string_guess)
    print(f"Let's see if you can find\nthe hidden word to guess:\n{final_string}")

    # verify if the guess interred is correct or not

    times = False
    limit = select_diff(level, times)
    win = False
    tries = 0
    while tries < limit and not win:
        guess = input("Enter you guess:\n> ").lower()
        if guess in words:
            print("Bingo ! good job you found it :)")
            score += 1
            win = True
        elif guess not in words:
            tries += 1
            print(f"you have {str(limit - tries)} guesses")
    if tries == limit:
        print("GAME OVER !")
    question = input("Do you wanna play again ?\n"
                     "> ").upper()
    if question == "YES":
        response = True
    elif question == "NO":
        print(f"your score is: {score}")
        print("thank you for playing :)")
        break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
