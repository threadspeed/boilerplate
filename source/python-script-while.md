---
title: python script while (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'while'


Modules used in program: 
* `import random`
* `import random`
* `import random`
* `import random`

## python while

Python mysql example: while

```python
# сколько разрядов в числе?

n = int(input("Введите число: "))
count = 0

while n > 0:
    n = n // 10
    count += 1

print(count)

# проверить, что пользователь не забыл заполнить поле в анкете

while True:
    mobile = input("Введите свой номер телефона: ")
    if mobile:
        print("Спасибо! С вами свяжутся.")
        break
    print("\nВы забыли ввести номер телефона.")

# Пользователь-экстрасенс угадывает число

import random

x = random.randint(1, 10)
check = True

while check:
    guess = int(input("Угадайте число от 1 до 10: "))
    check = guess != x # check станет False только в тот момент, когда пользователь введет число, которое равно загадонному

print("УРА!")

# Угадывание числа (с использованием break)

import random

x = random.randint(1, 10)

while True:
    guess = int(input("Угадайте число от 1 до 10: "))
    if guess == x:
        break

print("УРА!")

# набрать мелочь на проезд: есть только монеты в 1 и 2 рубля

import random

money_found = 0

while money_found < 28:
    money_found += random.randint(1, 2) 

print(money_found)

# мелочь на проезд, но в кармане только x монет

import random

money_found = 0
count = 0
coins = int(input("Сколько у вас монет: "))

while money_found < 28 and count < coins:
    money_found += random.randint(1, 2)
    count += 1

print(money_found, count)

if money_found >= 28:
    print("Успех")
else:
    print("Идем пешком")

# максимальная степень двойки, на которую делится число

n = int(input("Введите число: "))
count = 0

while n % 2 == 0:
    n = n // 2
    count += 1

print(count)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
