---
title: python script PythonExercicios ex028 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex028'


Modules used in program: 
* `import time`
* `import random`

## python PythonExercicios ex028

Python example: PythonExercicios ex028

```python
import random
import time
n = random.randint(0,5)
print('-=-' * 15)
print('Vou pensar em um número entre 0 e 5. Tente adivinhar: ')
print('-=-' * 15)
x = int(input('Em que número eu pensei? '))
print('PROCESSANDO...')
time.sleep(2)
if x == n:
    print('Parabéns, você acertou!')
else:
    print('O computador venceu. Eu escolhi o número {} e não o {}'.format(n, x))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
