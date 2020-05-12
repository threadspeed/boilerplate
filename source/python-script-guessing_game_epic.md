---
title: python script guessing game epic (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game epic'

Functions in program: 
* `def high_low(guess, number):`
* `def get_valid_number():`

## python guessing game epic

Python mysql example: guessing game epic

```python
def get_valid_number():
    while True:
        number = input("Pick a number 1-100: ")
        try:
            number = int(number)
            if number <= 100 and number >= 1:
                return number
            else:
                print("Your number should be between 1 and 100.")
        except ValueError:
            print("That's not an integer.")


def high_low(guess, number):
    if guess > number:
        return "high"
    else:
        return "low"


guess_range = [1, 100]
guesses = 0
number = get_valid_number()
while True:
    guesses += 1
    guess = int(sum(guess_range)/2)
    if guess == number:
        print(number, "was the correct answer. The computer wins.")
        print("Guesses: ", guesses)
        break
    elif guess > number:
        print("The guess {} is too high".format(guess))
        guess_range[1] = guess
    else:
        print("The guess {} is too low.".format(guess))
        guess_range[0] = guess
    if guesses == 5:
        print("That was five guesses. The computer loses.")
        break

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
