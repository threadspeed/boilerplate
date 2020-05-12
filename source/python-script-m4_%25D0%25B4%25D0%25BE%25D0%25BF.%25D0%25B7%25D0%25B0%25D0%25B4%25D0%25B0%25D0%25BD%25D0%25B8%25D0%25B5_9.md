---
title: python script m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 9 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 9'


Modules used in program: 
* `import math`

## python m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 9

Python mysql example: m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 9

```python
#9. Составьте программу, которая выводит на экран календарь на любой
#месяц по заданному году. Воспользуйтесь алгоритмом вычисления дня
#недели, описанном в лабораторной работе 5.

from calendar import monthrange
import math

print("Программа выводит календарь за заданный год и месяц")

year = int(input("Введите год: "))
month = int(input("Введите номер месяца: "))

daysInMonth = monthrange(year, month)

days = [
    [None] * 7,
    [None] * 7,
    [None] * 7,
    [None] * 7,
    [None] * 7,
    [None] * 7
]

print("%6s %4s %4s %4s %4s %4s %4s" %("Пн.", "Вт.", "Ср.", "Чт.", "Пт.", "Сб.", "Вс."))
fistDayIndex = daysInMonth[0]
day = 1
index = fistDayIndex
for i in range(6):
    for j in range(index, 6 + 1):
        if day > daysInMonth[1]:
            break
        days[i][j] = day
        day += 1
        index += 1
        if index > 6:
            index = 0
            break

for i in range(len(days)):
    for j in range(len(days[i])):
        if days[i][j] == None:
            print("%5s" % (" "), end="")
        else:
            print("%5s" % (days[i][j]), end="")
    print("")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
