---
title: python script 009 Guessing Game One (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '009 Guessing Game One'


Modules used in program: 
* `import random`

## python 009 Guessing Game One

Python example: 009 Guessing Game One

```python
# Exercise (and Solution)

# Generate a random number between 1 and 9 (including 1 and 9).
# Ask the user to guess the number, then tell them whether they guessed too low, too high, or exactly right.
# (Hint: remember to use the user input lessons from the very first exercise)

# Extras:

# Keep the game going until the user types “exit”
# Keep track of how many guesses the user has taken, and when the game ends, print(this out.)

import random

print("\n\n\t\t~~~~~~~~~~~~~~~~~~~~~~ Guessing GAME ~~~~~~~~~~~~~~~~~~~~~~")
count = 0
ls = []
while True:
    ch = int(input("\nGuess a number from: 1 to 9.\n"))
    r = random.randint(1, 9)
    ls.append(ch)
    print(" * * * * * Computer's number was: ", r, " * * * * * ")
    if ch == r:
        print("\nDamn! You're awesome. Correct guess.")
    elif ch > r:
        print("\nA little too high.")
    elif ch < r:
        print("\nA little too low.")

    print("\n\n- - - - - - - - - - - - - - - - - - - - - - - - - -")
    choice = input("Press any key to play or \"exit\" to quit the game.\n"
                   "- - - - - - - - - - - - - - - - - - - - - - - - - -\n").lower()
    if choice == "exit":
        print("Your guesses were: ", end= " ")
        for i in ls:
            print(i, end=" ")
        print("\nThanks for playing!")
        break
    else:
        print("\n\n- - - - - - - - - - - - - - - - - - - - - - - - - -\nNew Game!")



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
