---
title: python script PythonExercicios ex035 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex035'


## python PythonExercicios ex035

Python mysql example: PythonExercicios ex035

```python
print('-=-' * 20)
print('Analisador de Triângulos')
print('-=-' * 20)
r1 = float(input('Digite um comprimento: '))
r2 = float(input('Digite outro comprimento: '))
r3 = float(input('Digite o último comprimento: '))
'''if n2 - n3 < n1 and n1 < n2 + n3:
    reta1 = True
else:
    reta1 = False
if n1 - n3 < n2 and n2 < n1 + n3:
    reta2 = True
else:
    reta2 = False
if n1 - n2 < n3 and n2 < n1 + n2:
    reta3 = True
else:
    reta3 = False
if reta1 and reta2 and reta3 == True:
    print('Com essas medidas, podemos formar um triângulo!')
else:
    print('Com essas medidas, não podemos formar um triângulo!')'''
if r1 < r2 + r3 and r2 < r1 + r3 and r3 < r1 + r2:
    print('Os segmentos acima PODEM FORMAR um triângulo!')
else:
    print('Os segmentos acima NÃO PODEM FORMAR um triângulo!')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
