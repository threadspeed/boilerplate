---
title: python script guess game1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess game1'


Modules used in program: 
* `import sys #Allows a new selection of system related commands to be used, I use sys.exit() to close the program`
* `import random #Allows the computer to generate random numbers, vital for the program to function correctly`

## python guess game1

Python mysql example: guess game1

```python
import random #Allows the computer to generate random numbers, vital for the program to function correctly
import sys #Allows a new selection of system related commands to be used, I use sys.exit() to close the program
print("Hello! In this game, you shall attempt to guess my number.") # What the user sees upon opening the program
ran_num = random.randint(1,20)
attempts = 1
guess = int(input("Make your guess!"))
while guess != ran_num:
  if guess < ran_num:
    print("Your Guess is lower than generated value.")
    attempts +=1
    guess = int(input("Make your guess!"))
  elif guess > ran_num:
    print("Your Guess is higher than generated value.")
    attempts +=1
    guess = int(input("Make your guess!"))
  elif guess > 20:
    print("Enter a valid number")
    guess = int(input("Make your guess!"))
  elif guess == ran_num:
    print("Well done! You gussed it in",attempts,"tries")
    #end = input()
    #sys.exit()
  elif attempts == 5:
    print("The number was", ran_num,"!")
    print("Maximum amount of tries reached!")
    sys.exit()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
