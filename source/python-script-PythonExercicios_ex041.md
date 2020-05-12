---
title: python script PythonExercicios ex041 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex041'


Modules used in program: 
* `import datetime`

## python PythonExercicios ex041

Python mysql example: PythonExercicios ex041

```python
import datetime
ano = int(input('Digite seu ano de nascimento: '))
idade = datetime.date.today().year - ano
if idade <= 9:
    print('Você tem {} anos, portanto sua categoria é MIRIM.'.format(idade))
elif idade <= 14:
    print('Você tem {} anos, portanto sua categoria é INFANTIL.'.format(idade))
elif idade <= 19:
    print('Você tem {} anos, portanto sua categoria é JUNIOR.'.format(idade))
elif idade <= 25:
    print('Você tem {} anos, portanto sua categoria é SÊNIOR.'.format(idade))
else:
    print('Você tem {} anos, portanto sua categoria é MASTER.'.format(idade))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
