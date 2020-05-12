---
title: python script guess the number (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess the number'


Modules used in program: 
* `import random`

## python guess the number

Python example: guess the number

```python
import random

guessNum = random.randint(1, 10)

guess = 3
while guess > 0:
	guess -= 1
	ask = int(raw_input("Guess the number: "))
	if ask < guessNum:
		print("Your guess is too low.")
	
	elif ask > guessNum:
		print("Your guess is too high.")
	
	elif ask == guessNum:
		print("You win!")
	
else:
	guessNum = str(guessNum)
	print("Nope. The number I was thinking of was " + guessNum + ".")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
