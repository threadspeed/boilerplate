---
title: python script escolha um da lista randomica (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'escolha um da lista randomica'


Modules used in program: 
* `import random`

## python escolha um da lista randomica

Python example: escolha um da lista randomica

```python
import random
print('Aluno Randomico escolhido\n')
al_1 = str(input('Digite o Nome do Primeiro aluno: '))
al_2 = str(input('Digite o Nome do Segundo aluno: '))
al_3 = str(input('Digite o nome do Terceiro aluno: '))
al_4 = str(input('Digite o nome do Quarto aluno: '))

lista = [al_1, al_2, al_3, al_4]
escolhido = random.choice(lista)

print(('\nO aluno escolhido foi: {}'.format(escolhido)))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
