---
title: python script untitled ex044 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex044'


Modules used in program: 
* `import datetime`

## python untitled ex044

Python mysql example: untitled ex044

```python
import datetime

maior = 0
menor = 0

for i in range(1, 8):
    p = int(input("Digite o ano de nascimento da {} pessoa: ".format(i)))
    if datetime.date.today().year - p >= 18:
        maior += 1
    else:
        menor += 1
print("{} pessoas são menores de idade e {} são maiores de idade.".format(menor, maior))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
