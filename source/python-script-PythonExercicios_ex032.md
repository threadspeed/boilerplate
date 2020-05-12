---
title: python script PythonExercicios ex032 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex032'


## python PythonExercicios ex032

Python mysql example: PythonExercicios ex032

```python
from datetime import date
ano = int(input('Em que ano você está? Coloque 0 para analisar o ano atual: '))
if ano == 0:
    ano = date.today().year
if ano % 4 == 0 and ano % 100 != 0 or ano % 400 == 0:
    print('O ano {} é Bissexto!'.format(ano))
else:
    print('O ano {} não é Bissexto!'.format(ano))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
