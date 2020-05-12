---
title: python script m4 9 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 9'


Modules used in program: 
* `import random;`

## python m4 9

Python example: m4 9

```python
#Задание 9
#Составить программу определения среднемесячной температуры
#воздуха, если известна средняя температура за каждый день месяца.
#Исходные данные для вычислений лучше использовать реальные.

import random;

print("Программа определения среднемесячной температуры воздуха")

monthInfo = [
    {'daysCount': 31, 'tempRange': [random.randrange(-38, -1) for i in range(31)],},
    {'daysCount': 29, 'tempRange': [random.randrange(-38, -1) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(0, 15) for i in range(31)],},
    {'daysCount': 30, 'tempRange': [random.randrange(0, 15) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(0, 15) for i in range(31)],},
    {'daysCount': 30, 'tempRange': [random.randrange(10, 35) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(10, 35) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(10, 35) for i in range(31)],},
    {'daysCount': 30, 'tempRange': [random.randrange(0, 20) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(0, 20) for i in range(31)],},
    {'daysCount': 30, 'tempRange': [random.randrange(0, 20) for i in range(31)],},
    {'daysCount': 31, 'tempRange': [random.randrange(-38, -1) for i in range(31)],}
]

infoFromKeyword = False # если стоит True то информацию о температура нужно будет вводить с клавиатуры, иначе она генерится случайно
monthTemperatures = [None]
month = int(input("Введите номер месяца для которого необходимо расчитать температуру: ")) - 1

if infoFromKeyword :
    monthTemperatures = [None] * monthInfo[month]['daysCount']
    for i in range(1, monthInfo[month]['daysCount'] + 1):
        monthTemperatures[i-1] = int(input("Введите температуру за " + str(i) + " д. " + str(month) + "мес.: "))
else:
    monthTemperatures = monthInfo[month]['tempRange']
    print("Информация о температуре за", month, "мес.:", monthTemperatures)

print("Cредняя температура за", month, "мес. =", sum(monthTemperatures)/monthInfo[month]['daysCount'])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
