---
title: python script Guessing game2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Guessing game2'


Modules used in program: 
* `import random`

## python Guessing game2

Python mysql example: Guessing game2

```python
import random

number = random.randint(1,99)
guesses = 0

while guesses < 5:
	guess = int(input("Enter an integer from 1 to 99 : "))
	print()
	guesses += 1
	print("this is your " +str(guesses) + " guess")

	if guess < number:
		print("guess is low")
	elif guess > number:
		print("guess is high")
	elif guess == number:
		break

if guess == number:
	guesses = str(guesses)
	print("you guess it in", guesses + " guesses")
elif guess != number:
	number = str(number)
	print("The secret number was", number)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
