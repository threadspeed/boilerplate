---
title: python script untitled ex030 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex030'


Modules used in program: 
* `import  datetime`

## python untitled ex030

Python example: untitled ex030

```python
import  datetime

ano = int(input("Digite o ano de nascimento do atleta: "))
atual = datetime.date.today().year - ano

if atual <= 9:
    print("O Atleta está classificado na modalidade MIRIM")
elif atual <= 14:
    print("O Atleta está classificado na modalidade INFANTIL")
elif atual <= 19:
    print("O Atleta está classificado na modalidade JUNIOR")
elif atual <= 25:
    print("O Atleta está classificado na modalidade SENIOR")
else:
    print(("O Atleta está classificado na modalidade MASTER"))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
