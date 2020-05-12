---
title: python script m4 11 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 11'


Modules used in program: 
* `import random;`

## python m4 11

Python example: m4 11

```python
# Задание 11
# У тренера футбольного клуба имеется список членов команды и
# количества очков, которые принес команде каждый игрок в данном
# сезоне. Составить программу, с помощью которой можно определить
# самого результативного игрока.

import random;

print("Программа для определения самого результативного игрока")

peopleCount = int(input("Введите количество играков: "))
infoFromKeyword = False if (input("Cгенерировать количество очков автоматически(да/нет): ") == "да") else True
points = [None] * peopleCount

if infoFromKeyword :
    for i in range(1, peopleCount + 1):
        points[i-1] = int(input("Введите количество очков для " + str(i) + " игрока: "))
else:
    for i in range(1, peopleCount + 1):
        points[i-1] = random.randrange(0, 100)
    print("Згенерировались следующие очки:", points)

maxIndex = points.index(max(points))
print("Самый результативный игрок под номером",maxIndex+1, ". Он имеет", points[maxIndex], "очк.")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
