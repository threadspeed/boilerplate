---
title: python script numberGuess (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'numberGuess'

Functions in program: 
* `def number_guess():`
* `def valid_num(s):`

Modules used in program: 
* `import random`

## python numberGuess

Python example: numberGuess

```python
import random
from unittest.mock import patch
from unittest import TestCase
from unittest import main


def valid_num(s):
    if type(s) == int and 1 <= int(s) <= 10:
        return True
    return False


def number_guess():
    number = random.randint(1, 10)
    guess = input("Guess a number between 1 and 10")
    print(number)
    if valid_num(guess):
        guess = int(guess)
        if guess < number:
            return "Too low"
        elif guess > number:
            return "Too high"
        return "You got the number!"
    return "You input and invalid number"


class Test(TestCase):
    @patch('builtins.input', return_value="am invalid")
    def test_validates_number(self, input):
        self.assertEquals(number_guess(), "You input and invalid number")

    @patch('random.randint', return_value=5)
    @patch('builtins.input', return_value=2)
    def test_notifies_too_low(self,  randint, input):
        self.assertEquals(number_guess(), "Too low")

    @patch('builtins.input', return_value=6)
    @patch('random.randint', return_value=5)
    def test_notifies_too_high(self,  randint, input):
        self.assertEquals(number_guess(), "Too high")


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
