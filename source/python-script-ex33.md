---
title: python script ex33 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex33'


## python ex33

Python mysql example: ex33

```python
n1=float(input('Digite o primeiro numero: '))
n2=float(input('Digite o segundo numero: '))
n3=float(input(('Digite o terceiro numero')))
if (n1>n2) and (n1>n3):
    maior=n1
if (n2>n1) and (n2>n3):
    maior=n2
else:
    maior=n3

if (n1<n2) and (n1<n3):
    menor=n1
if (n2<n1) and (n2<n3):
    menor=n2
else:
    menor=n3

if n1<maior and n1>menor:
    meio=n1
if n2<maior and n2>menor:
    meio=n2
else:
    maior=n3

print('a sequencia é : {} - {} - {}'.format(maior,meio,menor))






```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
