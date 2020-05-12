---
title: python script ex28 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex28'


Modules used in program: 
* `import random`

## python ex28

Python mysql example: ex28

```python
import random
n = random.randint(0, 5)
print('Estou pensando em um numero.....')
print('................................')
numero=int(input('Tente adivinhar o numero entre 0 e 5 que eu pensei: '))
while(numero != n):
     erros=1
     print('Voce errou, o numero que eu escolhi foi {}'.format(n))
     n = random.randint(0, 5)
     numero = int(input('Tente adivinhar o numero entre 0 e 5 que eu pensei: '))
     erros=erros+1

print('Voce acertou, o numero que escolhi foi {}, mas voce errou {} vezes'.format(n,erros))







```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
