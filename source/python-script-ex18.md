---
title: python script ex18 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex18'

Functions in program: 
* `def tan(x):`
* `def cos(x):`
* `def sen(x):`

Modules used in program: 
* `import math`

## python ex18

Python example: ex18

```python
import math

angulo=float(input('Digite o angulo:'))

def sen(x):
    seno = math.sin(x)
    return seno

def cos(x):
    cos = math.cos(x)
    return cos

def tan(x):
    tan = math.tan(x)
    return tan

print( 'O seno é {:.2} o cosseno é {:.2} e a tangente é {:.2}'.format(sen(angulo), cos(angulo), tan(angulo)))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
