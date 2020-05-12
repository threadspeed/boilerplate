---
title: python script ex068 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex068'


Modules used in program: 
* `import random`

## python ex068

Python mysql example: ex068

```python
import random
vitoria=0
derrota=False
pi='P'
while derrota==False:
    pi = str(input('Vamos jogar Par ou Impar? Escolha pár ou impar: [P/I]')).upper()
    while pi not in 'PI':
        print('Opcao errada! Tente novamente.')
        pi = str(input('Vamos jogar Par ou Impar? Escolha pár ou impar: [P/I]')).upper()
    n=int(input('Ok, escola seu numero de 1 a 10: '))
    while n > 11:
        print('Numero errado, tente novamente.')
        n = int(input('Ok, escola seu numero de 1 a 10: '))
    m= random.randint(0,10)
    soma=n+m
    if soma%2==0:
        resultado= 'P'
    else:
        resultado= 'I'
    if resultado == pi:
        print('Voce ganhou!')
        vitoria+=1
        derrota=False
    else:
        derrota=True
print(f'Meu numero foi {m} e o resultado da soma foi {soma}')
print(f'Voce ganhou {vitoria}')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
