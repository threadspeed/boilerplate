---
title: python script PythonExercicios ex054 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex054'


Modules used in program: 
* `import time`
* `import datetime`

## python PythonExercicios ex054

Python example: PythonExercicios ex054

```python
import datetime
import time
hoje = datetime.date.today().year
maior = 0
menor = 0
for ano in range(1,8):
    nasc = int(input('Digite o ano do seu nascimento: '))
    if hoje - nasc >= 21:
        maior += 1
    else:
        menor += 1
print('Processando...')
time.sleep(2)
print('{} pessoas atingiram a maioridade!'.format(maior))
print('{} pessoas não atingiram a maioridade!'.format(menor))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
