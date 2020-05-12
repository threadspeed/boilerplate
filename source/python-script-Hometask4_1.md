---
title: python script Hometask4 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Hometask4 1'

Functions in program: 
* `def gen_list(a):`

Modules used in program: 
* `import random`

## python Hometask4 1

Python example: Hometask4 1

```python
'''
Написать функцию, которая генерирует список списков (двух мерный массив) размерности NxN заполненный случайными числами от 100 до 999
(использовать функцию random.randint(100, 999)
пример
>>gen_list(2)
[[222, 113], [456, 500]]
'''

import random


def gen_list(a):
  return [[random.randint(10, 1000) for i in range(a)] for _ in range(a)]

gen_list(4)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
