---
title: python script guessing game two (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game two'


Modules used in program: 
* `import random`

## python guessing game two

Python mysql example: guessing game two

```python
import random

a = random.randint(0, 100)

guess = 0

while guess < 100:
	ask = int(raw_input("Guess the number: "))
	
	guess += 1
	if ask < a:
		print("You guessed too low.")
		
	if ask > a:
		print("You guessed too high.")

	if ask == a:
		guess = str(guess)
		print("You win! You guessed " + guess + " times.")
		break

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
