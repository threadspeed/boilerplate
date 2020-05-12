---
title: python script secret no (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'secret no'

Functions in program: 
* `def game():`
* `def evaluate(number, secret):`
* `def guess():`
* `def secretNumber():`
* `def game():`
* `def evaluate(number, secret):`
* `def guess():`
* `def secretNumber():`

## python secret no

Python mysql example: secret no

```python
from random import random

def secretNumber():
	return int(random() * 1000)

def guess():
	print('> ',)
	return input()

def evaluate(number, secret):
	if number == secret:
		print("You win!" )
		return True
	if number > secret:
		print("Guess Smaller!")
		return False
	if number < secret:
		print("Guess Bigger!")
		return False
	
def game():
	secret = secretNumber()
	for i in range(0,10):
		number = guess()
		won = evaluate(number, secret)
		if won: return
	print("You lose! The number was %s" % secret)
	
if __name__ == "__main__":
	print("10 chances to find secret no between 1 and 1000")
	game()from random import random

def secretNumber():
	return int(random() * 1000)

def guess():
	print('> ',)
	return input()

def evaluate(number, secret):
	if number == secret:
		print("You win!" )
		return True
	if number > secret:
		print("Guess Smaller!")
		return False
	if number < secret:
		print("Guess Bigger!")
		return False
	
def game():
	secret = secretNumber()
	for i in range(0,10):
		number = guess()
		won = evaluate(number, secret)
		if won: return
	print("You lose! The number was %s" % secret)
	
if __name__ == "__main__":
	print("10 chances to find secret no between 1 and 1000")
	game()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
