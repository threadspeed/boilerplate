---
title: python script ex041 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex041'


## python ex041

Python mysql example: ex041

```python
from datetime import date
ano = int(input('Digite a o ano de nascimento:'))
hoje = date.today()
anoAtual = str(date.strftime(hoje, "%Y"))
tempo = int(anoAtual) - ano
if tempo < 10:
    categoria = 'Mirin'
elif tempo > 9 and tempo < 15:
    categoria = 'Infantil'
elif tempo > 14 and tempo < 20:
    categoria = 'Junior'
elif tempo > 19 and tempo < 21:
    categoria = 'Senior'
else:
    categoria = 'Master'

print('O atelta esta na categoria {} com {} anos!'.format(categoria, tempo))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
