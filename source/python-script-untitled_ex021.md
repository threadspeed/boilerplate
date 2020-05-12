---
title: python script untitled ex021 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex021'


Modules used in program: 
* `import datetime`

## python untitled ex021

Python mysql example: untitled ex021

```python
import datetime

ano = int(input("Qual ano vc quer analisar ?, (Digite 0 para o ano atual): "))
if ano == 0:
    ano = datetime.date.today().year
if ano % 4 == 0 and ano % 100 != 0 or ano % 400 == 0:
    print('O amo {} é BISSEXTO'.format(ano))
else:
    print("O ano não é BISSEXTO".format(ano))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
