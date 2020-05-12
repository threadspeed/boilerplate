---
title: python script random student (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random student'


Modules used in program: 
* `import random`

## python random student

Python example: random student

```python
# Python Project: STUDENT NAME GENERATOR 
# PROMPT: BUILD A PYTHON CLI THAT TAKES IN A LIST OF STUDENTS AND RANDOMLY SELECTS ONE OF THEIR NAMES

# Import Random Number Generator
import random

# Print Welcome CLI Info
print('--------')
print('\nWelcome to the Class Randomizer!')

# Ask the User the for # of Students
num_players = input('\nEnter The Number of Students: ')
num_players = int(num_players);
print('\nNow Please Enter Each Students Name Individually')

# Enter Each Students Name
students = []
i=0
for i in range(num_players):
    player_name = input('\nEnter Name: ')
    students.append(player_name)
print('--------')

# Print Out Numbered List
for i in range(len(students)):
    print("\n"+str(i+1)+")"+students[i])

# Randomly Select a Student
print('--------')
print('\nRandomly Selected Student:')
random_student = students[random.randint(0,num_players-1)]

#Print Randomly Selected Student
print('\n'+random_student)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
