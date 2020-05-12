---
title: python script Number%2520Guessing%2520Game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Number%2520Guessing%2520Game'


Modules used in program: 
* `import random`

## python Number%2520Guessing%2520Game

Python mysql example: Number%2520Guessing%2520Game

```python
#Import random module
import random

#Assign a random integer to variable num - this is what the user has to guess
num = random.randint(1,100)

#Prompt user to give a guess
guess = int(raw_input("Give me a number between 1 and 100:"))

#Initialize count to be used in while loop
count = 1

#While loop that provides feedback on user's guesses until user guesses correctly
while count < 100:
    if guess == num:
        print("You win! You guessed right in %d guess(es)." % (count))
        break
    elif guess < num:
        print("You guessed too low.")
        count = count + 1
        guess = int(raw_input("Give me a number between 1 and 9:"))
    else:
        print("You guessed too high.")
        count = count + 1
        guess = int(raw_input("Give me a number between 1 and 9:"))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
