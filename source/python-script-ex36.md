---
title: python script ex36 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex36'


## python ex36

Python example: ex36

```python
valorCasa = float(input('Qual é o valor da casa? '))
valorSalario = float(input('Qual é seu salário atual? '))
intervalo = float(input(' Qual é o periodo (em anos) do emprestimo?'))
prestacao= valorCasa / (intervalo*12)
if prestacao > (valorSalario*0.3):
    print('O Empréstimo foi negado, pois a parcela de R$ {:4.2f} excede 30% do seu salario'.format(prestacao))
else:
    print('O valor da parcela é de R$ {:4.2f}'.format(prestacao))




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
