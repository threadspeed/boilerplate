---
title: python script function (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'function'

Functions in program: 
* `def get_your_move():`
* `def get_eagle_or_tails():`
* `def get_insert_name(name):`

Modules used in program: 
* `import random`
* `import random`

## python function

Python example: function

```python
#1. Подстановка вашего имя
#Представьте, вы пишите программу, чат-бота или разрабатываете User Interface, где вам нужно поздороваться с пользователем.
# Эту проблему можно решить с помощью функции:

def get_insert_name(name):
    greetings = "Hello,"
    full_greetings = greetings + name
    print(full_greetings)

get_insert_name("Oleh")


#2. Орел или решка
#Иногда, бывает нужно решить важный вопрос: "быть" или "не быть" и мы подкидываем монетку. Давайте сделаем своего помощника
#в тяжелом выборе, всего пару строк кода

import random

def get_eagle_or_tails():
    random_choices = ['Орел', 'Решка']
    response = random.choice(random_choices)
    print(response)

get_eagle_or_tails()

#3. Камень, Ножницы, Бумага, раз, два, три ...
#Наверное каждый играл в эту популярную по всему миру в игру. Иногда бывает скучно, развлечь себя нечем. Так вот, программист
#Петя, решил использовать недавно полученные навыки программирования и написать по-быстрому игру, посмотрим что с этого получилось.
import random

def get_your_move():
    random_choices = ['Камень', 'Ножницы', 'Бумага']
    response = random.choice(random_choices)
    print(response)

get_your_move()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
