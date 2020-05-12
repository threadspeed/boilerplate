---
title: python script ex17 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex17'

Functions in program: 
* `def calculo(a, b):`

Modules used in program: 
* `import math`

## python ex17

Python mysql example: ex17

```python
import math

catadj = float(input('Digite o cateto adjacente:'))
catopo = float(input('Digite o cateto oposto:'))


def calculo(a, b):
    hipo = math.hypot(a, b)
    return hipo

resultado= (calculo(catopo, catadj))
print('A Hipotenusa é:{:.3}'.format(resultado))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
