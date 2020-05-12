---
title: python script game04 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game04'

Functions in program: 
* `def main():`
* `def doom():`
* `def expert():`
* `def hard():`
* `def easy():`
* `def guess_loop(limit):`
* `def choice():`

Modules used in program: 
* `import random`

## python game04

Python mysql example: game04

```python
import random


def choice():
    user_choice = input("Continue to certain doom? Yes/No ").upper()
    if user_choice == "YES":
        print("Walking the corridors... \n" )
        return True
    else:
        print("Going home... \n")
        return False


def guess_loop(limit):
    random_number = random.randint(1, limit)
    guess = int(input("Guess the number: "))
    while guess != random_number:
        if guess > random_number:
            print("Try again number was too high!")
        else:
            print("Try again number was too low!")
        guess = int(input("I think the number is: "))


def easy():
    print("""
    # The Guess of Doooooom #\n
    The worst guessing game you\'ve ever played.
    By Matthew Hillman \n
    Can you beat Doom mode?
    """)
    print("Easy mode...1 to 10")
    guess_loop(10)
    print("\nCongratulations; you beat Easy mode!")


def hard():
    print("Hard Mode...1 to 100")
    guess_loop(100)
    print("\nCongratulations; you beat Hard mode!")


def expert():
    print("Expert Mode...1 to 1,000")
    guess_loop(1000)
    print("\nCongratulations; you beat Expert mode!")


def doom():
    print("DOOM Mode...1 to 10,000")
    guess_loop(10000)
    print("\nCongratulations; You must be the Devil himself.")


def main():
    easy()
    choice()
    hard()
    choice()
    expert()
    choice()
    doom()


if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
