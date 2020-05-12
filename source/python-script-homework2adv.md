---
title: python script homework2adv (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'homework2adv'

Functions in program: 
* `def player_choice():`
* `def too_high(number):`
* `def too_low(number):`
* `def random_number():`

Modules used in program: 
* `import random`

## python homework2adv

Python example: homework2adv

```python
import random


def random_number():
    num1 = int(input("What is the lowest number you want to be in your range? "))
    num2 = int(input("What is the highest number you want to be in your range? "))
    numbers = list(range(num1, num2 + 1))
    random.shuffle(numbers)
    answer = numbers[int(len(numbers) / 2)]
    return answer


def too_low(number):
    if number >= answer - 5:
        print("You're so close! Your guess was just a little too low. Guess again.")
    elif number >= answer - 10:
        print("You're close! Your guess was slightly too low. Guess again.")
    else:
        print("Your guess is too low! Guess again.")


def too_high(number):
    if number <= answer + 5:
        print("You're so close! Your guess was just a little too high. Guess again.")
    elif number <= answer + 10:
        print("You're close! Your guess was slightly too high. Guess again.")
    else:
        print("Your guess is too high! Guess again.")

answer = random_number()

def player_choice():
    num_of_tries = 5
    guesses = []
    guesses_too_high = []
    guesses_too_low = []
    while num_of_tries >= 0:
        print("You have {} tries left to guess my number.".format(num_of_tries))
        guess = input("Guess a number between 1 and 100. ")
        # could not get this to work with choosing your own range of numbers
        print("-" * 15)
        print()
        try:
            int(guess)
        except ValueError:
            print("You did not enter a valid number. Guess again.")
            continue

        guess = int(guess)

        if guess == answer:
            print("You guessed my number, you win!")
            break
        elif guess in guesses:
            print("You already guessed that... Are you okay?")
            continue
        elif guess < answer:
            too_low(guess)
            guesses_too_low.append(guess)
            if len(guesses_too_low) != 0 and guess < max(guesses_too_low):
                print("You just wasted a guess.")
                print("You already knew {} was too low.".format(max(guesses_too_low)))
        elif guess > answer:
            too_high(guess)
            guesses_too_high.append(guess)
            if len(guesses) != 0 and guess > min(guesses_too_high):
                print("You just wasted a guess.")
                print("You already knew {} was too high.".format(min(guesses_too_low)))

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
