---
title: python script m4 6 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 6'

Functions in program: 
* `def kvadrat(number):`

## python m4 6

Python example: m4 6

```python
# Задание 6
# Квадрат любого натурального числа N равен сумме первых N нечетных чисел:
# 1^2 = 1
# 2^2 = 1 + 3
# 3^2 = 1 + 3 + 5
# 4^2 = 1 + 3 + 5 + 7
# Проверьте, верна ли эта закономерность для других натуральных чисел.

def kvadrat(number):
     res = [x for x in range(1, number * 2 , 2)] # список нечетных чисел
     return sum(res)

print("Программа проверки закономерности  'Квадрат любого натурального числа N равен сумме первых N нечетных чисел'")

n = int(input("До какого числа проверять закономерность ?"))

print("Проверка будет выполнятся до числа =", n)
print("%2s %40s" % ("Обычный квадрат числа", "Квадрат с помощью суммирование"))

for i in range(1, n+1):
    print("%9s %40s" % (i**2, kvadrat(i)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
