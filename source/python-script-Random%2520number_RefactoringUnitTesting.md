---
title: python script Random%2520number RefactoringUnitTesting (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random%2520number RefactoringUnitTesting'

Functions in program: 
* `def compare(guess=0):`

Modules used in program: 
* `import re`
* `import random`

## python Random%2520number RefactoringUnitTesting

Python example: Random%2520number RefactoringUnitTesting

```python
#_*_Coding:utf-8_*_
import random
import re
def compare(guess=0):
    guessesTaken= 0
    out=0
    print('Hello! What is your name?')
    myName = input()
    number = int(random.randint(1, 100))
    print(number)
    print('Well, ' + myName + ', I am thinking of a number between 1 and 100.')
    while out==0:
        while 1:
            print('Take a guess.') # There are four spaces in front of print.
            guess = input()
            if guess== "q":
                return 4
                exit(0)
            if re.match('[a-zA-Z #$@%&\()*]', guess):           #filter alphbate
                print('pls only input number ssss between 0-100')
                return 0
                break
            if 1<=int(guess) and int(guess)<=100:
                guess=int(guess)
                guessesTaken = guessesTaken + 1
                if guess < number:
                    print('Your guess is too low.')
                    return 1
                elif guess > number:
                    print('Your guess is too high.')
                    return 2
                elif guess == number:
                    out=out+1
                    return 3
                    break
            else:
                print('pls input number between 0-100')
    if guess == number:
        guessesTaken = str(guessesTaken)
        print('Good job, ' + myName + '! You guessed my number in ' + guessesTaken + ' guesses!')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
