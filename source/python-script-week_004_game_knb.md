---
title: python script week 004 game knb (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 004 game knb'

Functions in program: 
* `def game():`
* `def print_output(result, person, comp):`
* `def translate(x):`

Modules used in program: 
* `import random`

## python week 004 game knb

Python example: week 004 game knb

```python
# 8
# версия с остатком по модулю

import random

def translate(x):
    if x == 1:
        return "камень"
    elif x == 2:
        return "ножницы"
    else:
        return "бумага"

def print_output(result, person, comp):
    print(result)
    print(person, "::", comp)

def game():
    person = int(input("Поиграем? Введите число: 1 - камень, 2 - ножницы, 3 - бумага\n"))
    comp = random.randint(1, 3)

    person_name = translate(person)
    comp_name = translate(comp)
    
    you_won = "Человек победил!"
    comp_won = "Компьютер победил!"
    draw = "Ничья!"

    diff = (person - comp) % 3

    if diff == 2:
        result = you_won
    elif diff == 1:
        result = comp_won
    else:
        result = draw

    print_output(result, person_name, comp_name)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
