---
title: python script week 003 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 003'

Functions in program: 
* `def hero():`
* `def f2d6():`
* `def f1d6():`
* `def measure_circle(r):`
* `def crazy_strings(s1, s2):`
* `def str_mult(x, n):`

Modules used in program: 
* `import random`
* `import random`
* `import math`

## python week 003

Python example: week 003

```python
# 1

def str_mult(x, n):
    print((str(x) + "\n") * n)

# 2

def crazy_strings(s1, s2):
    n1 = len(s1)
    n2 = len(s2)
    print(s1 * n2)
    print(s2 * n1)

# 3

import math

def measure_circle(r):
    circumference = round(2 * math.pi * r, 3)
    area = round(math.pi * (r ** 2), 3)
    return circumference, area

# 4

# подгружает библиотеку random
import random

# определение функции f1d6
def f1d6():
    d = random.randint(1, 6) # генерация случайного числа от 1 до 6 (подкидывание кубика)
    return d # просим функцию возвращать только что сгенерированное число

# определение функции f2d6
def f2d6():
    d = f1d6() + f1d6() # подкидывание двух кубиков и суммирование выпавших значений
    return d # просим функцию вернуть получившуюся сумму

res1 = f2d6() # подкинули два кубика, запомнили сумму выпавших значений
res2 = f2d6() # повторили
print('1: {}\n2: {}'.format(res1, res2)) # выводим на экран результаты в формате:
# 1: сумма выпавших значений в первое подкидывание
# 2: сумма выпавших значений во второй раз

# 5

'''

каждый кубик это значения от 1 до 6
следовательно их сумма может быть в диапазоне от 2 до 12

вероятность получить каждое из этих значений не одинакова,
т.к. существует только один способ получить значение 2 (по 1 на каждом кубике),
только один способ получить 12 (по 6 на каждом кубике),
но получить значения 7, 8, 9 гораздо проще, а значит и выпадать они будут чаще
7, например, получается из суммы 1 и 6, 2 и 5, 3 и 4

'''

# 6

'''
Сила, Ловкость, Интеллект, Выносливость, Харизма.
0<=Сила<=15,
0<=Ловкость<=15-Сила,
0<=Интеллект<=15-Сила-Ловкость и так далее, а на Харизму что осталось.

Урон = СИЛА*3 + ЛОВКОСТЬ*2
Здоровье = ВЫНОСЛИВОСТЬ*4 + СИЛА*1
Переносимый вес = ВЫНОСЛИВОСТЬ*2 + СИЛА*3
Красноречие = ХАРИЗМА*4 + ИНТЕЛЛЕКТ*1
'''

import random

def hero():
    strength = random.randint(0, 15)
    agility = random.randint(0, 15 - strength)
    intelligence = random.randint(0, 15 - strength - agility)
    endurance = random.randint(0, 15 - strength - agility - intelligence)
    charisma = random.randint(0, 15 - strength - agility - intelligence - endurance)
    print(("Параметры рыцаря:\nСила: %s \nЛовкость: %s \nИнтеллект: %s \nВыносливость: %s \nХаризма: %s" % (strength, agility, intelligence, endurance, charisma)))

    attack_damage = strength * 3 + agility * 2
    health = endurance * 4 + strength 
    can_carry = endurance * 2 + strength * 3
    eloquence = charisma * 4 + intelligence
    print(("\nНавыки рыцаря:\nУрон: %s\nЗдоровье: %s\nПереносимый вес: %s\nКрасноречие: %s" % (attack_damage, health, can_carry, eloquence)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
