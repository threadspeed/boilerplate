---
title: python script m4 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 2'


## python m4 2

Python example: m4 2

```python
# Задание 2
# В файле m4_2.py находится программа печати таблицы значений
# функции f(x) = sin(x) при x = 0, 0.1, 0.2,..., 2. Модифицируйте
# программу так, чтобы:
# а) печатался заголовок;
# б) печатались еще и значения аргумента x;
# в) печатались значения при x = 0, 0.2, 0.4, ..., 3;
# г) то же самое печаталось в обратном порядке.

from math import sin

print_x_first_variant = True #если стоит False то будет печататься строки со значениями при x = 0, 0.2, 0.4, ..., 3 иначе 0, 0.1, 0.2 .. 2.00
reversal = False # Если True то будет печататься в обратном порядке иначе будет печататься в обычном порядке

rangeSize = 21 if print_x_first_variant else 32
x = 2.00 if (print_x_first_variant and reversal) else 3.00 if (not (print_x_first_variant) and reversal) else 0
RANGE = reversed(range(0, rangeSize)) if reversal else range(0, rangeSize)

for i in RANGE:
    if (not(reversal) and i == 0) or (reversal and i == rangeSize-1):
        print("%2s %14s %21s" % ("Numbers", "x", "sin(x)"))
    if  (print_x_first_variant or (round(x,2)  == round(i*0.1, 2))):
        print("%4d %8s %10.2f %8s %10.4f" % (i, " - ", x, " - ", sin(x)))
        if not(print_x_first_variant):
            x = abs(x - 0.2) if reversal else x + 0.2
    if print_x_first_variant:
        x = abs(x - 0.1) if reversal else x + 0.1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
