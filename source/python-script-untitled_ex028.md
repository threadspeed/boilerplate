---
title: python script untitled ex028 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex028'


Modules used in program: 
* `import datetime`

## python untitled ex028

Python mysql example: untitled ex028

```python
import datetime

ano = int(input("Digite ano de seu nascimento:"))
idade = datetime.date.today().year - ano

if idade == 18:
    print("Jovem está na hora de se alistar")
elif idade < 18:
    print("Jovem ainda faltam {} anos para se alistar".format(18 - idade))
else:
    if idade > 45:
        print("Senhor tem {} anos e passou da idade de se alistar e está dispensado há {} ano(s)".format(idade,idade
                                                                                                         - 45))
    else:
        print("Senhor tem {} anos e passou da idade de se alistar e faltam {} para sair da reserva.".format(idade,
                                                                                                            45 -idade
                                                                                                            ))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
