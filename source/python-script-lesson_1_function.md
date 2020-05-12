---
title: python script lesson 1 function (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lesson 1 function'

Functions in program: 
* `def jock():`
* `def spaceship_bulding (cans):`
* `def varible_test():`
* `def savings (pocket_money, paper_route, spending):`
* `def newfunc(name, kname):`

Modules used in program: 
* `import  sys`
* `import time`
* `import random`

## python lesson 1 function

Python mysql example: lesson 1 function

```python
def newfunc(name, kname):
    print('Hello, %s, %s' % (name, kname))

newfunc('Dori', 'Koli')
import random
a = random.randint(0, 100)
b = random.randint(1000, 5000)

newfunc(a, b)

def savings (pocket_money, paper_route, spending):
    return pocket_money + paper_route - spending

money = savings(120, 50, 14)
print(money)
print(savings(120, 50, 14))

another_varibale =  5000
def varible_test():
    first_varibale = 10
    second_varibale =20
    return first_varibale * second_varibale * another_varibale
print(varible_test())

def spaceship_bulding (cans):
    total_cans = 0
    for week in range(1, 53):
        total_cans = total_cans + cans
        print('Неделя %s, банок: %s' % (week, total_cans))

import time
import  sys

def jock():
    print('Привет, друг! Ответь на простой вопрос: ' '\n'
          'Тебе есть 18 лет ?  да / нет')
    answer = sys.stdin.readline() #str(input())                      #(sys.stdin.readline())
    if answer == ('да') or answer == 'Да' or answer == 'ДА':
        print('Ок продолжим')
    else:
        print('Пошел нах пес !')

print(jock())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
