---
title: python script m4 7 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 7'

Functions in program: 
* `def factorial(n):`
* `def eval2(scale):`
* `def evalPI(scale):`
* `def evalE(scale):`

Modules used in program: 
* `import math`

## python m4 7

Python mysql example: m4 7

```python
# Задание 7
# Многие из математических величин или значений функций могут быть
# выражены как суммы бесконечных последовательностей. Чем больше
# членов ряда участвует в сложении, тем более точным получается
# искомое значение.
# Составьте программы и попытайтесь определить минимальное число
# членов ряда, обеспечивающих вычисление следующих данных:


import math

def evalE(scale):
    summ = 0
    count = 0
    while round(summ, scale)  != round(math.e, scale):
        summ += 1/factorial(count)
        count += 1
    return count

def evalPI(scale):
    summ = 0
    count = 1
    while round(summ, scale)  != round(math.pi / 4, scale):
        summ += ((-1)**(count - 1))/(2*count-1)
        count += 1
    return count

def eval2(scale):
    proiz = 1
    count = 1
    a = round((2**(1/2))/2, scale)
    while round(proiz, scale) != a:
        proiz *= (1 + (((-1)**count)/(2*count + 1)))
        count += 1
        # break
    return count

def factorial(n):
     if n == 0:
          return 1
     return factorial(n-1) * n


n = 6#int(input("Введите количество символов после запятой (необходимо для сравнения)"))

#Подсчет ряда e
print("Необходимо", evalE(n), "шагов для достижения числа e =", round(math.e, n))
#Конец подсчета ряда e
#Подсчет ряда корень из 2
print("Необходимо", eval2(n), "шагов для достижения числа корень из 2 =", round(2**(1/2), n))
#Конец подсчета корень из 2
#Подсчет ряда pi
print("Необходимо", evalPI(n), "шагов для достижения числа pi =", round(math.pi, n))
#Конец подсчета ряда pi


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
