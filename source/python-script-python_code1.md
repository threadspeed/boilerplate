---
title: python script python code1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'python code1'


Modules used in program: 
* `import random`

## python python code1

Python mysql example: python code1

```python
#Number Smart Game#

#Random module imported to access randint function 
import random
from random import randint
#initialising Variables
current_mistakes = 0
mistakes_allowed = 5
wins_needed = 3
one_ran_num = 0
two_ran_num = 0
guess = 0
big_num = 0
small_num = 0 
#CONSTANTS
MIN_NUMBER1 = 1
MAX_NUMBER1 = 50
#INCREASE LEVEL 1 to 2
level = 1
MAX_LEVEL = 2
#set random value to one_ran_num and two_ran_num
one_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
two_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
######two_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
if one_ran_num > two_ran_num:
    big_num = one_ran_num
    small_num = two_ran_num
elif one_ran_num < two_ran_num:
    big_num = two_ran_num
    small_num = one_ran_num

while one_ran_num == two_ran_num:
    one_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
    break
  
#Indrouce user and auto caps and spaces
user_name = input("What is your name?").title().strip()
print("Hi {} welcome to the Number Smart game where you need to choose the larger number 3 times to win the level!".format(user_name))

while current_mistakes < mistakes_allowed:
    while wins_needed != 0:
        guess = int(input("{}, you have {}, attempts to choose the larger number. \n You have {} victories needed to move the the next level. \n I’m thinking of {} and {}, which one is larger? \n".format(user_name, mistakes_allowed, wins_needed, one_ran_num, two_ran_num)))
        one_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
        two_ran_num = random.randint(MIN_NUMBER1, MAX_NUMBER1)
        if guess == big_num:
            wins_needed = wins_needed - 1
            print("That's Right! Next Question.\n")
            break
        elif guess == small_num:
            mistakes_allowed = mistakes_allowed - 1
            print("Wrong, that was the smaller number. Try again.\n")
            break
        elif guess < small_num:
            print("Please enter a number from the two")
            break
        elif guess > small_num:
            print("Please enter a number from the two")
            

    if wins_needed == 0:
        print("You have won level 1!")
        
    elif mistakes_allowed == current_mistakes:
        print("You have lost level 1")
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
