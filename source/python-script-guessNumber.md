---
title: python script guessNumber (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessNumber'


Modules used in program: 
* `import random`

## python guessNumber

Python example: guessNumber

```python
import random

#PC chooses and the Player guesses the number

lives = 9

#Prints how to play

print("\nOk, how to play:")
print("- I choose a number between 1 and 100.")
print("- You try to guess and i tell you Higher or Lower.")
print("- Do you have 9 lives")
input("(Press something to continue)")

myNumber = random.randint(1, 100)
input("\nWait, i am choosing one number. (Press something to continue)")
input("Ready! Let's start. (Press something to continue)")



#the guessing part, 4 types, wrong type (letters, negative numbers etc.), Higher, Lower and the chosen one.

while True:

	guess = 0
	try:
		guess = int(input("\n Enter a number: "))

	except:
		print("\n I don't think you've understood the game.")

	if (guess < 1 or guess > 100):
		example = random.randint(1, 100)
		print("\n One number between 1 and 100. Mmm... For example: " +
		      str(example))
	else:
		if (guess == myNumber):
			print(
			    "\n You win. It was " + str(myNumber) +
			    "\n It's not funny, It was supposed you have to lose. \n I hope to see you soon again."
			)
			break
		if (guess > myNumber):
			lives = lives - 1
			print("Lower! Left you " + str(lives) + " lives")
			input(" (Press something to continue.)")

		if (guess < myNumber):
			lives = lives - 1
			print("Higher! Left you " + str(lives) + " lives")
			input(" (Press something to continue.)")

		if (lives == 0):
			anotherNumber = random.randint(1000, 10000)
			print("\n 0 lives, The number was " + str(anotherNumber) +
			      ". Just kidding, i chose " + str(myNumber))
			print("I hope to see you soon again.")
			break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
