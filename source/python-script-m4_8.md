---
title: python script m4 8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 8'


Modules used in program: 
* `import random;`

## python m4 8

Python example: m4 8

```python
#Задание 8
#Для определения рентабельности авиалинии вычисляется среднее
#количество пассажиров за год. Составьте программу вычисления
#среднего количества пассажиров, перевезенных за год, если известно
#общее количество пассажиров, перевезенных за каждый месяц.

import random;

print("Программа подсчета среднего количества пассажиров перевезенных за год")

monthCount = 12
infoFromKeyword = False # если стоит True то информацию о кол-ве человек нужно будет вводить с клавиатуры, иначе она генерится случайно
колВо_чел_в_мес = [None]

if infoFromKeyword :
	колВо_чел_в_мес = [None] * monthCount
	for i in range(1, monthCount+1):
		колВо_чел_в_мес[i-1] = int(input("Введите количество человек перевезенных за " + str(i) + " мес.: "))
else:
	колВо_чел_в_мес = [random.randrange(0, 10) * 1050 for i in range(monthCount)]
	print("Информация о количестве перевезенных пассажиров за каждый месяц(по порядку):", колВо_чел_в_мес)

print("Среднее число человек перевезенных за", monthCount , "мес. =", sum(колВо_чел_в_мес)/monthCount)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
