---
title: python script week 004 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 004'

Functions in program: 
* `def hard_choice():`
* `def circle_hit_test(x, y, r = 5):`
* `def fireball(wizard, monster):`
* `def simple_calc():`
* `def compare_numbers():`
* `def get_sign(x):`

Modules used in program: 
* `import random`
* `import math # пожгружаем модуль math`
* `import random`

## python week 004

Python example: week 004

```python
# 1

def get_sign(x):
    if x > 0:
        return "+"
    elif x < 0:
        return "-"
    else:
        return "0"

# 2

def compare_numbers():
    a = int(input("Input first number: "))
    b = int(input("Input second number: "))
    if a == b:
        result = "="
    elif a > b:
        result = ">"
    else:
        result = "<"
    print(("%d %s %d" % (a, result, b)))

# 3

def simple_calc():
    a = int(input("Input first number: "))
    operator = input("Operator: ")
    b = int(input("Input second number: "))
    if operator == "+":
    	print(a + b)
    elif operator == "*":
        print(a * b)
    elif operator == "-":
        print(a - b)
    elif operator == "/":
	if b != 0:
        	print(a / b)
	else:
		print("Not possible to divide!")

# 4

import random

def fireball(wizard, monster):
    print(("%s casts a fireball at %s" % (wizard, monster)))
    x = random.randint(1,3)
    if x > 2:
        print("Miss")
    else:
        print("%s is hit for 20 damage" % monster)

# 5

import math # пожгружаем модуль math

d = int(input("Type a number: ")) # просим пользователя ввести число с клавиатуры и переводим полученную строку в числовой формат 

if d <= 0: # сравниваем введенное пользователем число с 0
    print(d ** 2) # В том случае, если оно отрицательно, то возводим в квадрат
else:
    print(math.sqrt(d)) # в противном случае извлекаем из него корень
	

# 6

def circle_hit_test(x, y, r = 5):
    return x ** 2 + y ** 2 <= r ** 2

# 7

import random

def hard_choice():
    murka = random.randint(1, 20)
    zhuchka = random.randint(1, 20)
    print(murka, "\n", zhuchka)
    if murka <= 10 and zhuchka <= 10:
        print("Робот Вася идёт домой")
    elif murka > zhuchka:
        print("Робот Вася гладит кошку Мурку")
    elif zhuchka > murka:
        print("Робот Вася гладит собаку Жучку")
    else:
        print("Робот Вася гладит кошку Мурку и собаку Жучку")
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
