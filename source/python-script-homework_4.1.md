---
title: python script homework 4.1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'homework 4.1'


Modules used in program: 
* `import datetime`
* `import json # Required to read and write json elements`
* `import random`

## python homework 4.1

Python example: homework 4.1

```python
# Homework 4.1: Add some more data in the dictionary

import random
import json # Required to read and write json elements
import datetime

secret = random.randint(1, 30) # Random integer
attempts = 0

current_time = datetime.datetime.now()

with open("score_list.txt", "r") as score_file:
    score_list = json.loads(score_file.read())

for score_dict in score_list:
    print(str(score_dict["attempts"]) + " attempts, date: " +
          str(score_dict["date"]) + ", player name: " +
          score_dict["name"].title())

while True:
    guess = int(input("Guess the secret number (between 1 and 30): "))
    attempts += 1

    if guess == secret:
        print("Congratulations! It's number " + str(secret) + ".")
        print("Attempts needed: " + str(attempts))

        name = input("Please enter your name: ").lower()

        score_list.append({"attempts": attempts, "date": str(current_time),
                           "name": name})
        with open("score_list.txt", "w") as score_file:
            score_file.write(json.dumps(score_list))
        break
    elif guess > secret:
        print("Sorry! Try something smaller.")
    elif guess < secret:
        print("Sorry! Try something bigger.")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
