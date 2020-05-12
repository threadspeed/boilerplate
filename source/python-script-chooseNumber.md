---
title: python script chooseNumber (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'chooseNumber'


Modules used in program: 
* `import random`

## python chooseNumber

Python example: chooseNumber

```python
import random

#Player chooses and the PC guesses the number

#Variables, min and max for set the random guess.
minNumber = 1
maxNumber = 100
lives = 9

print(
    "\n Good! Please choose one number between 1 and 100 \n I will close my eyes"
)

#Select a number

while True:

	yourNumber = 0
	try:
		yourNumber = int(input("Choose your number: "))

	except:
		print("\n I'm not sure if do you want to play with me.")

	if (yourNumber < 1 or yourNumber > 100):
		example = random.randint(1, 100)
		print("\n One number between 1 and 100. Mmm... For example: " +
		      str(example))
	else:
		input(
		    "\n Awesome! We can play now. I will try to guess your number. 9 lives, maybe i'm a cat, a smart one! (Press something to continue.)"
		)
		break


#Guess the number, 4 ways, invalid one, lower, higher and the chosen number.
while True:

	number = random.randint(minNumber, maxNumber)
	print("\n Mmm... " + str(number) + "?")
	if (number == yourNumber):
		print(
		    "\n I win. It was " + str(yourNumber) +
		    "\n I forgot to tell you i can read minds. Muahaha. \n I hope to see you soon again."
		)
		break
	if (number > yourNumber):
		lives = lives - 1
		print("Lower? Ok, " + str(lives) + " lives left")
		input(" (Press something to continue.)")
		maxNumber = number - 1

	if (number < yourNumber):
		lives = lives - 1
		print("Higher? Ok, " + str(lives) + " lives left")
		input(" (Press something to continue.)")
		minNumber = number + 1
	if (lives == 0):
		print(
		    "\n 0 lives, I going to win next time, I hope to see you soon again."
		)
		break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
