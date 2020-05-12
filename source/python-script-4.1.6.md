---
title: python script 4.1.6 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '4.1.6'


Modules used in program: 
* `import random`

## python 4.1.6

Python example: 4.1.6

```python
import random

my_number = random.randint(0,10)
guess = -1

while True:
  guess = int(input())
  if guess > my_number: print("My number is smaller, try again")
  elif guess < my_number: print("My number is greater, try again")
  elif guess == my_number:
    print("Congratulations, you guessed right, it's {}!".format(my_number))
    break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
