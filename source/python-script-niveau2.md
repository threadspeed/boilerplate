---
title: python script niveau2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'niveau2'


Modules used in program: 
* `import random`

## python niveau2

Python mysql example: niveau2

```python
import random

keys = 0
snake_jar = random.randint(1, 5)

while keys != 3:
    choice = int(input("Choisit une jarre : 1, 2, 3, 4, 5"))
    if choice == snake_jar:
        keys -= 1
        print("Perdu ! vous tombez dans le piège (", keys, "/3) !")
    else:
        keys += 1
        print("Gagné ! vous avez obtenu une clé (", keys, "/3) !")

print("Tu deviens roi du temple")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
