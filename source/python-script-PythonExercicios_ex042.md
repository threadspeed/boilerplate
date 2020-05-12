---
title: python script PythonExercicios ex042 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex042'


## python PythonExercicios ex042

Python example: PythonExercicios ex042

```python
print('-=-' * 20)
print('Analisador de Triângulos')
print('-=-' * 20)
r1 = float(input('Digite um comprimento: '))
r2 = float(input('Digite outro comprimento: '))
r3 = float(input('Digite o último comprimento: '))

if r1 < r2 + r3 and r2 < r1 + r3 and r3 < r1 + r2:
    print('Os segmentos acima PODEM FORMAR um triângulo ', end='')
    '''if r1 == r2 and r2 == r3 and r1 == r3:
        print('O triângulo a ser formado será o EQUILÁTERO pois, todos os lados são iguais!')
    elif r1 == r2 or r1 == r3 or r2 == r3:
        print('O triângulo a ser formado será o ISÓSCELES pois, dois lados são iguais!')
    else:
        print('O triângulo a ser formado será o Escaleno pois, todos os lados são diferentes!')'''
    # Forma ensinada pelo Guanabara!
    if r1 == r2 == r3:
        print('EQUILÁTERO!')
    elif r1 != r2 != r3 != r1:
        print('ESCALENO!')
    else:
        print('ISÓSCELES!')
else:
    print('Os segmentos acima NÃO PODEM FORMAR um triângulo!')



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
