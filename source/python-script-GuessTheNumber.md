---
title: python script GuessTheNumber (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GuessTheNumber'


Modules used in program: 
* `import random`

## python GuessTheNumber

Python mysql example: GuessTheNumber

```python
# Program where the user has to guess the number in the given number of lives.
# User inputs the difficulty which determines the range the number is generated from.
# User also inputs the number of guesses they feel they need.

# import random package
import random

# Print welcome to the game
print("Hello, welcome to the number guessing game.")

# Ask user their chosen difficulty
while True:
    difficulty = input("What difficulty would you like? Please pick from the following: Easy, Medium, Hard: ").strip().lower()

# If difficulty not inputted from the options then tell them to state the difficulty until they do.
    if difficulty not in ["easy", "medium", "hard"]:
        print("Please can you state what difficulty you would like..?")
        continue

# Print out the ranges the user will be guessing between based on the difficulty they have inputtedq
    if difficulty == "easy":
        print("You have chosen 'Easy'. You will be guessing a number between 1 and 10.")
        break
    elif difficulty == "medium":
        print("You have chosen 'Medium'. You will be guessing a number between 1 and 20.")
        break
    elif difficulty == "hard":
        print("You have chosen 'Hard'. You will be guessing a number between 1 and 30.")
        break

# Ask user the number of lives they would like to have and only allow integer input values
while True:
    try:
        lives = int(input("How many lives or attempts would you like to have?: "))

    except ValueError:
        print("Please can you provide a number..")
        continue
        
    else:
        print("You will have {} attempts to guess the correct number. Goodluck.".format(lives))
        break

# Store random number based on difficulty for which the user has to guess
if difficulty == "easy":
    number = int(random.randint(1,10))

elif difficulty == "medium":
    number = int(random.randint(1,20))

else:
    number = int(random.randint(1,30))

# User's guesses
while lives > 0:

# Get user to input a guess and make sure they have to input a integerqqqq
    while True:
        try:
            guess = int(input("Please guess a number...: "))

        except ValueError:
            print("Please can you provide a number..")
            continue
        
        else:
            break

# If guess is equal to the number then print(congratulations to the user with the number of attempts they had remaining)
    if guess == number:
        print("Congratulations, you guessed the number correctly with {} attempt(s) left!".format(lives))
        break

# Otherwise, reduce the number of lives by one and give them a clue as to whether they should be guessing higher or lower
    else:
        lives = lives - 1
        if guess < number:
              print("Please guess higher...")
        else:
              print("Please guess lower...")
        print("You only have {} attempt(s) remaining...".format(lives))

# When number of attempts have ran out, then print(the correct number they were trying to get to.)
if lives == 0:
    print("Sorry, you weren't able to guess the correct number. The correct number was {}.".format(number))
              
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
