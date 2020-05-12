---
title: python script m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 4'

Functions in program: 
* `def soversh(n):`

## python m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 4

Python example: m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 4

```python
#4. Напишите программу вычисления совершенных чисел, не
#превосходящих заданного числа N. Совершенным называется такое
#число, сумма делителей которого совпадает с самим числом (например, 
#6=1+2+3).

print("Программа для вычисления совершенных чисел не превосходящих заданного числа N")

n = int(input("Введите число N: "))
k = 0

def soversh(n):
    s = 0
    j = 1
    while  j <= n/2:
        if n % j == 0 :
            s += j
        j += 1
    if s == n:
        return 1
    else:
        return 0

for i in range(1, n + 1):
    if soversh(i) != 0 :
        print(i)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
