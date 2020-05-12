---
title: python script guess game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess game'


Modules used in program: 
* `import random`

## python guess game

Python mysql example: guess game

```python
import random
myName = input("Hello what is your name : ")
number = random.randint(1,20)  #Computer will generate a number in between 1 and 20
print("Well, " + myName + ", I'm thinking a number beween 1 and 20. ")
guesstaken =0 
while guesstaken < 5: #I'm allowing the user for five trails
    print('Take a guess.')
    guess = int(input()) #Guess inputs

    guesstaken += 1
    if guess < number:
        print("Your guess is too low !!!")
    elif guess >number:
        print("Your guess is too high !!!")
    elif guess == number:

        break
if guess == number :
    guesstaken = str(guesstaken)
    print('Woow!!! Goood job '+ myName + "! you got my number ")
if guess != number :
    number = str(number)
    print("You did not get it right !!!" + " I was thinking "+ number)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
