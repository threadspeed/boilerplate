---
title: python script PythonExercicios ex018 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex018'


## python PythonExercicios ex018

Python example: PythonExercicios ex018

```python
'''import math
ang = float(input('Digite um ângulo qualquer: '))
sin = math.sin(ang)
cos = math.cos(ang)
tan = math.tan(ang)
print('Seno é {:.3f}'.format(sin))
print('Cosseno é {:.3f}'.format(cos))
print('E a tangente é {:.3f}'.format(tan))'''

from math import radians, sin, cos, tan
a = float(input('Digite um ângulo qualquer: '))
s = sin(radians(a))
print('O ângulo de {} tem o SENO de {:.2f}'.format(a, s))
c = cos(radians(a))
print('O ângulo de {} tem o COSSENO de {:.2f}'.format(a, c))
t = tan(radians(a))
print('O ângulo de {} tem a TANGENTE de {:.2f}'.format(a, t))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
