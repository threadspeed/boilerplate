---
title: python script guess solved (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess solved'

Functions in program: 
* `def get_random_number():`

Modules used in program: 
* `import random`

## python guess solved

Python example: guess solved

```python
"""
Javított működőképes változat, ami átmegy a teszteken, de lehetne még finomítani :-) 
A teszthez  a nevet át kell irni a test_guess.py fájlban (vagy guess.py-ként menteni ezt):
- from guess import get_random_number, Game
+ from guess_solved import get_random_number, Game
"""

import random
MAX_GUESSES = 5
START, END = 1, 20


def get_random_number():
    """Get a random number between START and END, returns int"""
    return random.randint(START, END)


class Game:
    """Number guess class, make it callable to initiate game"""

    def __init__(self):
        """Init _guesses, _answer, _win to set(), get_random_number(), False"""
        self._guesses = []
        self._answer = get_random_number()
        self._answer = 13
        self._win=False

    def guess2(self):
        """Ask user for input, convert to int, raise ValueError outputting
           the following errors when applicable:
           'Please enter a number'
           'Should be a number'
           'Number not in range'
           'Already guessed'
           If all good, return the int"""
        while True:
            g = input("Guess a number between 1 and 20:")
            try:
                if not g:
                    raise ValueError
                else:
                    try:
                        guess = int(g)
                        try:
                            if guess < START or guess > END:
                                raise ValueError
                            else:
                                try:
                                    if guess in self._guesses:
                                        raise ValueError
                                    else:
                                        self._guesses.append(guess)
                                        return guess
                                except ValueError:
                                    print("Already guessed")
                                    continue
                        except ValueError:
                            print("Number not in range")
                            continue

                    except ValueError:
                        print("Should be a number")
                        continue
            except ValueError:
                print("Please enter a number")
                continue

    def guess(self):
        """Ask user for input, convert to int, raise ValueError outputting
           the following errors when applicable:
           'Please enter a number'
           'Should be a number'
           'Number not in range'
           'Already guessed'
           If all good, return the int"""
        while True:
            g = input("Guess a number between 1 and 20:")
            try:
                if not g:
                    raise ValueError("Please enter a number")
                else:
                    try:
                        guess = int(g)
                        try:
                            if guess < START or guess > END:
                                raise ValueError("Number not in range")

                            if guess in self._guesses:
                                raise ValueError("Already guessed")
                            else:
                                self._guesses.append(guess)
                                return guess
                        except ValueError as e:
                            raise
                    except ValueError:
                        raise
            except ValueError as e:
                raise

    def _validate_guess(self, guess):
        """Verify if guess is correct, print(the following when applicable:)
           {guess} is correct!
           {guess} is too low
           {guess} is too high
           Return a boolean"""
        if guess<self._answer:
            print("{} is too low".format(guess))
            return False
        elif guess>self._answer:
            print("{} is too high".format(guess))
            return False
        else:
            print("{} is correct!".format(guess))
            self._win=True
            return True

    def __call__(self):
        """Entry point / game loop, use a loop break/continue,
           see the tests for the exact win/lose messaging"""
        while True:
            try:
                guess= self.guess()
            except ValueError as ve:
                print(ve)
                continue

            #self._validate_guess(guess)
            if self._validate_guess(guess):
                print('It took you {} guesses'.format(len(self._guesses)))
                break
            if len(self._guesses)>=MAX_GUESSES:
                print('Guessed 5 times, answer was {}'.format(self._answer))
                break
            else:
                continue


if __name__ == '__main__':
     game = Game()
     game()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
