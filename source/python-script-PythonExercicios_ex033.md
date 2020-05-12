---
title: python script PythonExercicios ex033 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex033'


## python PythonExercicios ex033

Python mysql example: PythonExercicios ex033

```python
print('Qual é o maior e o menor número dentre os 3 digitados?')
n1 = int(input('Digite um número: '))
n2 = int(input('Digite outro número: '))
n3 = int(input('Digite outro número: '))
'''if n1 > n2:
    maior = n1
else:
    maior = n2
if n3 > maior:
    maior = n3
print('O maior número é {}'.format(maior))
if n1 < n2:
    menor = n1
else:
    menor = n2
if n3 < menor:
    menor = n3

print('O menor número é {}'.format(menor))'''
# Testando menor valor
menor = n1
if n2 < n1 and n2 < n3:
    menor = n2
if n3 < n1 and n3 < n2:
    menor = n3
print('O menor valor digitado é {}'.format(menor))
# Testando maior valor
maior = n1
if n2 > n1 and n2 > n3:
    maior = n2
if n3 > n1 and n3 > n2:
    maior = n3
print('O maior valor digitado é {}'.format(maior))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
