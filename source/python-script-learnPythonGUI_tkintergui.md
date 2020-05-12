---
title: python script learnPythonGUI tkintergui (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'learnPythonGUI tkintergui'


Modules used in program: 
* `import random`

## python learnPythonGUI tkintergui

Python mysql example: learnPythonGUI tkintergui

```python
import random

guessNumber = True

userName = input("What is your name?")

number = random.randint(1, 100)
print(userName + ", guess a number between 1 and 30.")

guess = input()

while guessNumber == True:
    if int(guess) == number:
    	print("you guessed it!")
    	break
    	
    if int(guess) > number:
        print("your guess is too high")
    	
    if int(guess) < number:
        print("your guess is too low")
        
    else:
        print("wrong! try again.")
    guess = input()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
