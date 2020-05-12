---
title: python script secret%2520number (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'secret%2520number'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python secret%2520number

Python mysql example: secret%2520number

```python
print("Welcome to the secret number game!")
import random
def main():
    secret = random.randint(1, 30)

    while True:
        guess = int(raw_input("Guess the secret number (between 1 and 30): "))

        if guess == secret:
            print("You guessed it - congratulations! It's number %s :)" % secret)
            break
        elif guess > secret:
            print("Sorry, your guess is too high... Please try again.")
        elif guess < secret:
            print("Sorry, your guess is too low... Please try again.")




if __name__ == "__main__":  
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
