---
title: python script PythonExercicios ex031 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex031'


## python PythonExercicios ex031

Python mysql example: PythonExercicios ex031

```python
d = float(input('Qual será a distância da sua viagem? '))
print('Você está prestes a começar uma viagem de {:.2f}Km'.format(d))
'''if d <= 200:
    print('O valor da sua viagem vai custar R${}'.format(d * 0.50))
else:
    print('O valor da sua viagem vai custar R${}'.format(d * 0.45))'''
preço = d * 0.50 if d <= 200 else d * 0.45
print('O valor da sua viagem vai custar R${:.2f}'.format(preço))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
