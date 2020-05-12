---
title: python script game01 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game01'


Modules used in program: 
* `import random`

## python game01

Python mysql example: game01

```python
import random

random_number = random.randint(1, 10)

user = int(input("Guess the number: "))

while user != random_number:
    if user > random_number:
        print("Try again number was too high!")
    else:
        print("Try again number was too low!")
    user = int(input("Guess the number: "))
print("Well done!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
