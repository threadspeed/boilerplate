---
title: python script Hometask4 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Hometask4 2'

Functions in program: 
* `def print_list(a):`

## python Hometask4 2

Python mysql example: Hometask4 2

```python
'''
Написать функцию, которая выводит двухмерный список в виде таблицы
Пример
>>print_list([[222, 113], [456, 500]])
—————
| 222 | 113 |
—————
| 456 | 500 |
—————
'''

my_list = [[222, 144], [333, 555]]


def print_list(a):
    print(len(str(a[0])) * '—')
    print(' | ', a[0][0], '|', a[0][1], ' |')
    print(len(str(a[0])) * '—')
    print(' | ', a[1][0], '|', a[1][1], ' |')
    print(len(str(a[0])) * '—')


print_list(my_list)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
