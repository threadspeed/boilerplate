---
title: python script game05 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game05'

Functions in program: 
* `def main():`
* `def guess_loop(limit):`
* `def choice():`

Modules used in program: 
* `import random`

## python game05

Python example: game05

```python
import random


def choice():
    user_choice = input("Continue to certain doom? Yes/No ").upper()
    if user_choice == "YES":
        print("Walking the corridors... \n")
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


def main():
    all_levels = [
        {
            'name': 'Easy mode...',
                    'limit': 10
        },
        {
            'name': 'Hard mode...',
                    'limit': 100
        },
        {
            'name': 'expert mode...',
                    'limit': 1000
        },
        {
            'name': 'DOOM mode...',
                    'limit': 10000
        }
    ]

    print("""
# The Guess of Doooooom #\n
The worst guessing game you\'ve ever played.
By Matthew Hillman \n
Can you beat Doom mode?
""")

    for level in all_levels:
        # print('level name 1 to level limit)
        print('{} 1 to {}'.format(level['name'], level['limit']))
        guess_loop(level['limit'])
        print('Congratulations; you beat {}!\n'.format(level['name']))
        if choice() != True:
            break


if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
