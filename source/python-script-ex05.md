---
title: python script ex05 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex05'

Functions in program: 
* `def tran(m):`
* `def tranmm(m1):`
* `def media(x,y):`

Modules used in program: 
* `import math`

## python ex05

Python mysql example: ex05

```python


import math



num1 = float(input('Digite um numero'))
ant = num1 - 1
suc = num1 + 1

print("O antecessor de {:.2f} é {:.2f} e o sucessor é {:.2f}".format(num1, ant, suc))

num2 = float(input('\nDigite mais um numero:'))
print('a Raiz quadrada é {}'.format(int(num2**(1/2))))
print('o dobro de {0} é {1} e o triplo é {2}'.format(num2, (num2*2), (num2*3)))
#===============================================================================================
nota1 = float(input('Digite a Primeira nota: '))
nota2 = float(input(' Digite a segunda nota: '))


def media(x,y):
    m: float = (x+y)/2
    math.ceil(m)
    return m
    pass


print('A média entre {} e {} é de {:.1f}'.format(nota1, nota2, media(nota1,nota2)))

#================================================================================================

medida= (int(input('Digite a Distancia em metros: ')))


def tranmm(m1):
    mm= m1*1000
    return mm


def tran(m):
    cm = m*100
    return cm

print('Transformando {} metros, obtemos {} cm e {} mm'.format(medida, tran(medida), tranmm(medida)))

#================================================================================================

numTabuada: int = input('Digite um numero: ')
for i in range(10):
    print(' A tabuada de {} é \n {} x {} = {} \n'.format(numTabuada, numTabuada, i, (numTabuada*i)))
















```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
