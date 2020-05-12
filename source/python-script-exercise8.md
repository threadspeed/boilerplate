---
title: python script exercise8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise8'

Functions in program: 
* `def ask_if_continue():`
* `def player2_wins():`
* `def player1_wins():`

## python exercise8

Python example: exercise8

```python
def player1_wins():
	print('\n\n\t\t\t\tPlayer1 wins!!\n\n' )
	
def player2_wins():
	global player2_won
	player2_won = 1	
	print('\n\n\t\t\t\tPlayer2 wins!!\n\n' )

def ask_if_continue():
	go_on = int((raw_input('Do you want to continue? Press 1 for yes, 0 for no.:')))
	return go_on

while True:
	global player2_won
	player2_won = 0

	choice1 = int((raw_input("Player 1, enter your choice(Rock =1 ,Paper = 2 , Scissors = 3 ):")))
	choice2 = int((raw_input("Player 2, enter your choice(Rock =1 ,Paper = 2 , Scissors = 3 ):")))
	
	if(choice1 == choice2):
		print('\n\n\t\t\tPlayer-2 must select a different option than player-1\n\n\n')
		break

	if (choice1 == 1 and choice2 == 2):
		player2_wins()
		Continue = ask_if_continue()
		if (Continue == 0):
			break
	if (choice1 == 2 and choice2 == 3):
		player2_wins()	
		Continue = ask_if_continue()
		if (Continue == 0):
		 break
	if (choice1 == 3 and choice2 == 1):
		player2_wins()
		Continue = ask_if_continue()
		if (Continue == 0):
		 break
	if(player2_won == 0):
		player1_wins()
		Continue = ask_if_continue()
		if (Continue == 0):
		 break

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
