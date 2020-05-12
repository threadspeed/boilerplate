---
title: python script EnkelList (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'EnkelList'


Modules used in program: 
* `import json`
* `import random`

## python EnkelList

Python mysql example: EnkelList

```python
import random
import json

secret = random.randint(1, 30)
attempts = 0

with open("score_list.txt", "r") as score_file:
    score_list = json.loads(score_file.read())
    score_list.sort()
    print("Top scores: " + str(score_list[:3]))

while True:
    guess = int(input("Guess the secret number (between 1 and 30): "))
    attempts += 1

    if guess == secret:
        print("You've guessed it - congratulations! It's number " + str(secret))
        print("Attempts needed: " + str(attempts))

        score_list.append(attempts)

        with open("score_list.txt", "w") as score_file:
            score_file.write(json.dumps(score_list))
        break
    elif guess > secret:
        print("Your guess is not correct... try something smaller")
    elif guess < secret:
        print("Your guess is not correct... try something bigger")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
