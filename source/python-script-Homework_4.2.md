---
title: python script Homework 4.2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Homework 4.2'


Modules used in program: 
* `import datetime`
* `import json`
* `import random`

## python Homework 4.2

Python mysql example: Homework 4.2

```python
import random
import json
import datetime

secret = random.randint(1, 5)
intentos = 0
nombre = str(input("¿Como te llamas?:"))

with open("score_file.txt", "r") as score:
    score_list = json.loads(score.read())
    print("Top scores: " + str(score_list))
while True:
    guess = int(input("Guess the secret number (between 1 and 5): "))
    intentos = intentos + 1
    wrong_guesses = intentos - 1

    if guess == secret:
        score_list.append({"intentos": intentos, "fecha": str(datetime.datetime.now()), "nombre": nombre, "secret number": secret, "wrong_guesses": wrong_guesses})
        with open("score_file.txt", "w") as score:
            score.write(json.dumps(score_list))
        print("You've guessed it - congratulations! It's number " + str(secret))
        print("Attempts needed: " + str(intentos))
        break
    elif guess > secret:
        print("Your guess is not correct... try something smaller")
    elif guess < secret:
        print("Your guess is not correct... try something bigger")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
