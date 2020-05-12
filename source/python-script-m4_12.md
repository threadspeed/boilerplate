---
title: python script m4 12 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 12'

Functions in program: 
* `def maxFibon(maxElem):`
* `def fibon(count):`

Modules used in program: 
* `import random`

## python m4 12

Python example: m4 12

```python
#Составить программу, которая:
#а) выводит первые N чисел Фибоначчи; 
#б) определяет, сколько кроликов будет через М месяцев; через G лет; 
#в) позволит определить номер члена последовательности, значение
#которого превосходит заданное число К; 
#г) представить ряд Фибоначчи графически. Например:

import random
from tkinter import *

def fibon(count):
    a = 0
    b = 1
    for i in range(count):
        a, b = b, a + b
    return a
def maxFibon(maxElem):
    a = 0
    b = 1
    i = 0
    while maxElem >= a:
        a,b = b, a + b
        i += 1
    return {"index": i, "value": a}

print("Программа для работы с числами фибоначи")

numberCount = int(input("Сколько чисел Фибоначи выводить: "))
monthCount = int(input("Узнать сколько кроликов будет через(введите число месяцев): "))
yearCount = int(input("Узнать сколько кроликов будет через(введите число лет): "))
maxElem = int(input("Введите число К: "))

a = 0
b = 1
fib = [None] * numberCount
for i in range(numberCount):
    a, b = b, a + b
    fib[i] = a
print("Числа Фибоначи:", fib)
print("Через", monthCount, "мес. будет", fibon(monthCount+2), "крол.")
print("Через", yearCount, "год/лет будет", fibon(yearCount*12+2), "крол.")
maxF = maxFibon(maxElem)
print("Значение превосходящее число К(", maxElem, ") =",maxF["value"], "и имеет индекс", maxF["index"])
qwe = Tk()
qwe.title("Фибоначи")
qwe.geometry('800x600')
asd = Canvas(qwe, bg='white', width=800, height=600)
asd.pack()
a = 0
b = 1
color = ["red", "blue", "magenta", "lightgreen", "yellow", "lightblue"]
for i in range(numberCount):
    a, b = b, a + b
    colorIndex = random.randint(0,5)
    asd.create_rectangle(0, i*10, a*10,(i+1)*10,fill=color[colorIndex])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
