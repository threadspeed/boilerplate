---
title: python script guessinggame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessinggame'


Modules used in program: 
* `import random`

## python guessinggame

Python example: guessinggame

```python
#GuessingGame.py
#import random module
#generate random number from 1-10
#store the number in a variable, which will be the secrete number
#ask user to guess number from 1-10
#use a while to compare the secret number to the user's number
# as long as the user's guess is not equal to the secret number kee checkigng
#let the user know that they have guess the number, then quit
#tell user guess is too low or too high


import random
n = random.randint (1,10)
guess = int(input("enter a number from 1 to 10"))
while n != "guess":
    print
    if guess > n:
        print("guess is too high")
        guess = int(input("enter a number from 1 to 10"))
    elif guess < n:
        print("guess is too low")
        guess = int(input("enter a number from 1 to 10"))
    else:
        print("you have guessed the correct number!")
        break  


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
