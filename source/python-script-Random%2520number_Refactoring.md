---
title: python script Random%2520number Refactoring (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random%2520number Refactoring'

Functions in program: 
* `def compare(guess=0):`

Modules used in program: 
* `import random`
* `import re                               #new lib`

## python Random%2520number Refactoring

Python example: Random%2520number Refactoring

```python
#_*_Coding:utf-8_*_
import re                               #new lib
import random
def compare(guess=0):
    guessesTaken= 0
    out=0
    print('Hello! What is your name?')
    myName = input()
    number = int(random.randint(1, 100))
    print(number)
    print('Well, ' + myName + ', I am thinking of a number between 1 and 100.')
    while out==0:                                               #setting the interrupter to prevent circulating forever
        while 1:
            print('Take a guess.')
            guess = input()
            if guess== "q":
                print('u quit')
                exit()
            if re.match('[a-zA-Z #$@%&\()*]', guess):           #regulation about arbitrary input letters and signals
                print('pls only input number between 0-100')
                break
            if 1<=int(guess) and int(guess)<=100:               # optimizing the switch of 'guess' type
                guess=int(guess)
                guessesTaken = guessesTaken + 1
                if guess < number:
                    print('Your guess is too low.')
                elif guess > number:
                    print('Your guess is too high.')
                elif guess == number:
                    out=out+1
                    break
            else:
                print('pls input number between 0-100')
    if guess == number:
        guessesTaken = str(guessesTaken)
        print('Good job, ' + myName + '! You guessed my number in ' + guessesTaken + ' guesses!')
compare()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
