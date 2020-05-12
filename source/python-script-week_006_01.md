---
title: python script week 006 01 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 006 01'

Functions in program: 
* `def game():`
* `def input_int(text):`
* `def exercise():`
* `def calculate(a, operator, b):`
* `def check_password(corr_pw, n):`

Modules used in program: 
* `import random`
* `import random`

## python week 006 01

Python mysql example: week 006 01

```python
# 1

yes = ["хорошо", "ладно", "ок", "так и быть", "куплю"]
answer = input('Мама, купи мне новый айфон.\n')

while answer.lower() not in yes:
    answer = input('Мама, купи мне новый айфон.\n')
print("YEEEEEEES!")

# 2

guess = input("Что зимой и летом одним цветом?")
while guess.lower() != "ель":
    guess = input()

# 3

def check_password(corr_pw, n):
    pw = input("Введите пароль.\n")
    while pw != corr_pw and (n - 1):
        n -= 1
        pw = input("Введите пароль еще раз. Осталось попыток: %d\n" % n)
    return pw == corr_pw

# 4

import random

def calculate(a, operator, b):
    if operator == "+":
        result = a + b
    elif operator == "*":
        result = a * b
    elif operator == "-":
        result = a - b
    return result

def exercise():
    ops = ['+', '-', '*']

    a = random.randint(0, 9)
    b = random.randint(0, 9)
    op = ops[random.randint(0, 2)]

    true_result = calculate(a, op, b)
    user_result = input("%d %s %d = ?\n" % (a, op, b))
    
    while user_result != str(true_result):
        user_result = input("Try again!\n")

    print("Hurrah!")

# 5

import random

def input_int(text):
    try:
        return int(input(text))
    except ValueError:
        print("I accept only integers. Try again.")
        return input_int(text)

def game():
    num = random.randint(1, 100)
    # print(num)
    n = 5
    
    guess = input_int("Угадайте число от 1 до 100. У вас есть %d попыток.\n" % n)
    while num != guess and (n - 1):
        if guess > num:
            print("Меньше!")
        else:
            print("Больше!")
        n -= 1
        guess = input_int("Осталось попыток: %d\n" % n)
    if num == guess:
        print("Ура! Вы угадали число!")
    else:
        print("Увы. Повезет в следующий раз!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
