---
title: python script m4 10 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 10'


Modules used in program: 
* `import random;`

## python m4 10

Python mysql example: m4 10

```python
# Задание 10
# В память компьютера вводят по очереди координаты N точек.
# Определить координаты точки, максимально удаленной от начала
# координат

import random;

print("Программа для определения максимально удаленной точки от начала координат")

pointCount = int(input("Введите количество точек: "))
infoFromKeyword = False if (input("Cгенерировать координаты точек автоматически(да/нет): ") == "да") else True
places = [None] * pointCount

if infoFromKeyword :
    for i in range(1, pointCount + 1):
        x = int(input("Введите x точки №" + str(i) + ": "))
        y = int(input("Введите y точки №" + str(i) + ": "))
        places[i-1] = {'x': x, 'y': y}
else:
    for i in range(1, pointCount + 1):
        places[i-1] = {'x': random.randrange(-20, 20), 'y': random.randrange(-20, 20)}
    print("Згенерировались следующие точки c координатами:", places)

length = [None] * pointCount
for i in range(1, pointCount + 1):
    length[i-1] = (places[i-1]['x']**2+places[i-1]['y']**2)**(1/2)
maxPointIndex = length.index(max(length))
print("Максимально удаленна точка от начала имеет координаты: ", places[maxPointIndex])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
