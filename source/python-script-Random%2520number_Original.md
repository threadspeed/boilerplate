---
title: python script Random%2520number Original (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random%2520number Original'

Functions in program: 
* `def compare():`

Modules used in program: 
* `import random`

## python Random%2520number Original

Python example: Random%2520number Original

```python
#_*_Coding:utf-8_*_
import random
def compare():
    guessesTaken= 0
    print('Hello! What is your name?')
    myName = input()
    number = int(random.randint(1, 100))
    print(number)
    print('Well, ' + myName + ', I am thinking of a number between 1 and 100.')
    while 1:
        print('Take a guess.') # There are four spaces in front of print.
        guess = input()
        guessesTaken = guessesTaken + 1
        if guess =='q':
            print('u quit')
            quit(0);
        if int(guess) < number:
            print('Your guess is too low.') # There are eight spaces in front of print.
        if int(guess) > number:
            print('Your guess is too high.')
        if int(guess) ==int(number):
            guess=int(guess)
            break
    if guess == number:
        guessesTaken = str(guessesTaken)
        print('Good job, ' + myName + '! You guessed my number in ' + guessesTaken + ' guesses!')

compare()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
