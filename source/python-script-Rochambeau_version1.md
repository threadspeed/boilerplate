---
title: python script Rochambeau version1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Rochambeau version1'


Modules used in program: 
* `import random`

## python Rochambeau version1

Python mysql example: Rochambeau version1

```python
#PRE-REQUISITES:
#variables (set equal to user input)
#user input
#import random and random.choice function
#boolean logic (AND) (or nested IF's)
#multiple conditions (if else and 3 elif's)
#WHILE True (but not absolutely necessary)


import random

while True:

    user_choice = input("What do you want to choose: 'R', 'P', or 'S'? ")
    print(("You chose ", user_choice))
    options = ["r","p","s"]
    computer_choice = random.choice(options)
    print(("The computer chose ", computer_choice))
    if user_choice == computer_choice:
        print(("It was a Draw"))
    elif user_choice == "r" and computer_choice == "p":
        print(("Computer Wins"))
    elif user_choice == "p" and computer_choice == "s":
        print(("Computer Wins"))
    elif user_choice == "s" and computer_choice == "r":
        print(("Computer Wins"))
    else: 
        print(("You Win!"))
    print(("\n"))
    
    
# if user_choice == "r" and computer_choice == "s":
#     print(("You Win"))
# if user_choice == "p" and computer_choice == "r":
#     print(("You Win"))
# if user_choice == "s" and computer_choice == "p":
#     print(("You Win")   )
    







```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
