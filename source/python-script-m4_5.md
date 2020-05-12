---
title: python script m4 5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 5'

Functions in program: 
* `def factorial(n):`

## python m4 5

Python mysql example: m4 5

```python
# Задание 5
# Составьте программу вычисления n!, которая должна работать для
# любого вводимого n.
# Протестируйте работоспособность программы для очень большого
# числа и для n=0 (правило для 0 прописано выше).

# на мой взгляд самым подходящим способом для вычисления факториала
# является рекурсия
def factorial(n):
     if n == 0:
          return 1
     return factorial(n-1) * n

print("Программа нахождения факториала")
n = int(input("Введите n = "));

print("Факториал", n, "=", factorial(n))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
