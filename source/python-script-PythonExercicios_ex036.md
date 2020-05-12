---
title: python script PythonExercicios ex036 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex036'


## python PythonExercicios ex036

Python mysql example: PythonExercicios ex036

```python
casa = float(input('Digite o valor da casa: '))
salário = float(input('Digite o seu salário: '))
anos = int(input('Digite em quantos anos você pretende financiar a casa: '))
meses = anos * 12
exc = salário * (30 / 100)
prest = casa / meses
if prest > exc:
    print('Seu empréstimo foi negado pois a prestação excede 30% do seu salário.')
else:
    print('Financiamento aprovado. A casa será parcelada em {} meses e o valor da prestação será de R${:.2f}/mês.'.format(meses, casa / meses))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
