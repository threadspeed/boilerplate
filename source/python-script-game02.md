---
title: python script game02 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game02'

Functions in program: 
* `def main():`
* `def doom():`
* `def expert():`
* `def hard():`
* `def choice():`
* `def easy():`

Modules used in program: 
* `import random`

## python game02

Python mysql example: game02

```python
import random

random_number = random.randint(1, 10)

user = ""


def easy():
    print("""
    # The Guess of Doooooom #\n
    The worst guessing game you\'ve ever played.
    By Matthew Hillman \n
    Can you beat Doom mode?
    """)
    print("Easy mode...")
    user = int(input("Guess the number between 1 and 10: "))
    while user != random_number:
        if user > random_number:
            print("Try again number was too high!")
        else:
            print("Try again number was too low!")
        user = int(input("I think the number is: "))
    print("Well done!")


def choice():
    user_choice = input("Continue to certain doom? Yes/No").upper()
    if user_choice == "YES":
        print("Walking the corridors... \n" )
    else:
        print("Going home... \n")
        exit()


def hard():
    print("Hard Mode...")
    random_number = random.randint(1, 50)
    user = int(input("Guess the number from 1 to 50: "))

    while user != random_number:
        if user > random_number:
            print("Try again number was too high!")
        else:
            print("Try again number was too low!")
        user = int(input("I think the number is: "))
    else:
        print("Well done! Next level")


def expert():
    print("""
    Expert mode...\n
    Getting smart are we? Try this.
    """)
    random_number = random.randint(1, 10000)
    user_expert = int(input("Guess the number from 1 to 10,000: "))

    while user != random_number:
        if user > random_number:
            print("Too high")
        else:
            print("Too low")
        user = int(input("I think the number is: "))
    print("Congrats!")


def doom():
    print("Activating Doom Mode...")
    random_number = random.randint(1, 100000)
    user = int(input("Guess the number from 1 to 100,000: "))

    while user != random_number:
        if user > random_number:
            print("Too high")
        else:
            print("Too low")
        user = int(input("Guess the number: "))
    print("You must be the Devil himself. Well done.")


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
