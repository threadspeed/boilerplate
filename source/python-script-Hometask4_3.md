---
title: python script Hometask4 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Hometask4 3'

Functions in program: 
* `def list_90(a):`
* `def list_90(a):`
* `def list_max_num(a):`
* `def list_replase_num(a):`
* `def list_replase_d(a):`
* `def gen_list(a):`

Modules used in program: 
* `import random`

## python Hometask4 3

Python mysql example: Hometask4 3

```python
'''
Сгенерировать список размером 10х10 с помощью функции задания 1
-Заменить по главной диагонали все числа на 0
-Заменить все четные числа на 1, не четные на 0
-Вывести строку таблицы с максимальной суммой элементов
-Повернуть таблицу на 90 градусов, по часовой, против часовой
'''

import random


def gen_list(a):
  return [[random.randint(10, 1000) for i in range(a)] for _ in range(a)]


# -Заменить по главной диагонали все числа на 0
def list_replase_d(a):
    for i in range(len(a)):
        a[i][i] = 0
        print(a[i])


# -Заменить все четные числа на 1, не четные на 0

def list_replase_num(a):
    for i in range(len(a)):
        for j in range(len(a)):
            if a[i][j] % 2 == 0:
                a[i][j] = 1
            else:
                a[i][j] = 0
        print(a[i])


# -Вывести строку таблицы с максимальной суммой элементов

def list_max_num(a):
    print(max(a))


# -Повернуть таблицу на +90 градусов

def list_90(a):
    for i in range(len(a)):
      new_list = []
      for j in range(len(a)):
          new_list.insert(i,a[j][i])

      print(new_list)

list_90(gen_list(5))

# -Повернуть таблицу на -90 градусов

def list_90(a):
    o = len(a)-1
    for i in range(len(a)):
      list2 = []
      s = len(a)-1
      for _ in range(len(a)):
          list2.insert(i,a[s][o])
          s -= 1
      o -= 1
      print(list2)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
