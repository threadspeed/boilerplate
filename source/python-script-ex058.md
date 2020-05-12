---
title: python script ex058 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex058'


Modules used in program: 
* `import random`

## python ex058

Python mysql example: ex058

```python
import random
n = random.randint(0, 11)
print('Estou pensando em um numero.....')
print('................................')
numero=int(input('Tente adivinhar o numero entre 0 e 10 que eu pensei: '))
erros=0
print(n)
while(numero != n):
    numero = int(input('Voce errou, tente adivinhar o numero entre 0 e 10 que eu pensei: '))
    erros=erros+1

print('Voce acertou, o numero que escolhi foi {}, mas voce errou {} vezes'.format(n,erros))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
