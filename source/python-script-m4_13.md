---
title: python script m4 13 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 13'


Modules used in program: 
* `import random`

## python m4 13

Python example: m4 13

```python
#Задание 13
#Используя конструкцию цикла со счетчиком,
#самостоятельно составьте программу рисования
#детской игрушечной пирамидки (вид сбоку). 
#Убедитесь, что число элементов пирамидки может быть любое и при
#больших значения она не превращается в гантелю...


import random

from tkinter import *

print("Программа рисование пирамиды")
numberCount = int(input("Введите количество прямоугольников: "))
color = ["red", "blue", "magenta", "lightgreen", "yellow", "lightblue"]

qwe = Tk()
qwe.title("Фибоначи")
qwe.geometry('800x600')
asd = Canvas(qwe, bg='white', width=800, height=600)
asd.pack()

xc = 10
y = (numberCount+2)*xc+(numberCount - 3)*xc
x=0
for i in range( numberCount):
    colorIndex = random.randint(0,5)
    asd.create_rectangle(x, y-xc*i-xc, y,y-xc*i+xc,fill=color[colorIndex])
    x += xc
    y -= xc
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
