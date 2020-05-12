---
title: python script PythonExercicios ex019 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex019'


## python PythonExercicios ex019

Python example: PythonExercicios ex019

```python
'''import random
a1 = input('Primeiro aluno: ')
a2 = input('Segundo aluno: ')
a3 = input('Terceiro aluno: ')
a4 = input('Quarto aluno: ')
s = random.choice([a1, a2, a3, a4])
print(s)'''
from random import choice
a1 = input('Primeiro aluno: ')
a2 = input('Segundo aluno: ')
a3 = input('Terceiro aluno: ')
a4 = input('Quarto aluno: ')
alunos = [a1, a2, a3, a4]
s = choice(alunos)
print('O aluno(a) escolhido foi {}'.format(s))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
