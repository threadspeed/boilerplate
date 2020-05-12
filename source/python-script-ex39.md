---
title: python script ex39 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex39'


## python ex39

Python mysql example: ex39

```python
from datetime import date

ano = int(input('Digite a o ano de nascimento:'))
hoje =date.today()
anoAtual=str(date.strftime(hoje, "%Y"))
tempo = int(anoAtual) - ano
print(type(tempo))
if tempo == 17:
    print('Voce tem que se alistar esse ano.')
elif tempo < 17:
    print('Voce tem que se alistar somente em {}'.format(17 - tempo + int(anoAtual)))
elif tempo > 17:
    print('Voce deveria ter se alistado em {}'.format(int(anoAtual) - (tempo - 17)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
