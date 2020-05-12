---
title: python script RockPaperScissorsPythV3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RockPaperScissorsPythV3'

Functions in program: 
* `def comp_Choise():`

Modules used in program: 
* `import random`
* `import sys`

## python RockPaperScissorsPythV3

Python mysql example: RockPaperScissorsPythV3

```python
# Made for Python version 3 and up

import sys
import random

# Rock, paper scissors

# Declare global
# Program will run until this global has a value of 1
glob_WinLose = 0

# Start game
print("Welcome to rock, paper, scissors. To play, type 'r' for rock, 'p' for paper and 's' for scissors.\n")

def comp_Choise():
	#Generate a random response
	response = random.randint(1, 3)
	if response == int('1'):
		return "r"
	elif response == int('2'):
		return "p"
	elif response == int('3'):
		return "s"

while glob_WinLose == 0:
	user_Input = input("Rock, paper or scissor?\n")	
	# Get the computer response
	comp_Answer = comp_Choise()
	comp_PickedR = None	
	
	if comp_Answer == "r":
		comp_PickedR = "Rock"
	elif comp_Answer == "p":
		comp_PickedR = "Paper"
	elif comp_Answer == "s":
		comp_PickedR = "Scissor"
	
	print("The computer picked: " + comp_PickedR)
	
	if user_Input.lower() == comp_Answer:
		print(("It's a draw!"))
	else:
		if user_Input.lower() == "r":
			if comp_Answer == "p":
				print("Paper beats rock, you lose!")
				glob_WinLose = 1
			elif comp_Answer == "s":
				print("Rock beats scissor, you win!")
				glob_WinLose = 1
		elif user_Input.lower() == "p":
			if comp_Answer == "r":
				print("Paper beats rock, you win!")
				glob_WinLose = 1
			elif comp_Answer == "s":
				print("Scissors beat paper, you lose!")
				glob_WinLose = 1
		elif user_Input.lower() == "s":
			if comp_Answer == "r":
				print("Rock beats scissors, you lose!")
				glob_WinLose = 1
			elif comp_Answer == "p":
				print("Scissors beats paper, you win!")
				glob_WinLose = 1
		else:
			print(("Please type 'r', 'p' or 's'.\n"))
			
input("Thanks for playing! Press any key to exit.\n")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
