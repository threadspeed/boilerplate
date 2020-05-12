---
title: python script 9 guessing game one (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '9 guessing game one'


Modules used in program: 
* `import random`
* `import random`
* `import random`

## python 9 guessing game one

Python mysql example: 9 guessing game one

```python
# Generate a random number between 1 and 9 (including 1 and 9). Ask the user to guess the number, then tell them whether they guessed too low, too high, or exactly right.
import random
number = random.randint(1, 9)
user = int(input("Guess the number: "))
if number < user:
    print("You guessed too high")
elif number > user:
    print("You guessed too low")
elif number == user:
    print("You guessed right!")

# EXTRAS 1
# Keep the game going until the user types “exit”
import random
number = random.randint(1, 9)
endgame = False
while endgame is False:
    user = int(input("Guess the number: "))
    if number < user:
        print("You guessed too high")
    elif number > user:
        print("You guessed too low")
    elif number == user:
        print("You guessed right!")
        break
    endgame1 = input("If you want to exit type exit: ")
    if endgame1 == "exit":
        endgame = True
    elif endgame1 != "exit":
        endgame = False

#EXTRAS 2
# Keep track of how many guesses the user has taken, and when the game ends, print(this out.)
import random
number = random.randint(1, 9)
endgame = False
guesses = 0
while endgame is False:
    user = int(input("Guess the number: "))
    if number < user:
        print("You guessed too high")
        guesses += 1
    elif number > user:
        print("You guessed too low")
        guesses += 1
    elif number == user:
        print("You guessed right!")
        guesses += 1
        print("Number of guesses:", guesses)
        break
    endgame1 = input("If you want to exit type exit: ")
    if endgame1 == "exit":
        print("Number of guesses:", guesses, "Better luck next time :)")
        endgame = True
    elif endgame1 != "exit":
        endgame = False


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
