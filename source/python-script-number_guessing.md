---
title: python script number guessing (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'number guessing'


Modules used in program: 
* `import random as r`

## python number guessing

Python example: number guessing

```python
import random as r
response = "y"
right_guesses = 0
while response != "n":
    num = r.randint(1, 9)
    guess = int(input("Guess the number:"))
    print("Correct number:" + str(num))
    if num < guess:
        print("You guessed too high!!")
    elif num > guess:
        print("You guessed too low!!")
    else:
        print("You guessed exactly right!!")
        right_guesses = right_guesses + 1
    response = input("Do you wish to continue? (y/n)")
print("You guessed correctly exactly " + str(right_guesses) + " times!!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
