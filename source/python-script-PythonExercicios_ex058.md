---
title: python script PythonExercicios ex058 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex058'


Modules used in program: 
* `import random`

## python PythonExercicios ex058

Python mysql example: PythonExercicios ex058

```python
import random
pc = random.randint(0,10)
c = 1
print('''Olá, sou seu computador!
Acabei de pensar em um número entre 0 e 10.
Será que você consegue adivinhar qual foi?''')
user = int(input('Qual é o seu palpite?'))
while user != pc:
    if user < pc:
        print('Mais...')
    else:
        print('Menos...')
    c += 1
    user = int(input('Palpite errado. Tente novamente: '))
print('Parabéns, acertou com {} tentativa(s)'.format(c))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
