---
title: python script untitled ex025 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex025'


## python untitled ex025

Python mysql example: untitled ex025

```python
casa = float(input('Digite o valor final da casa: '))
salario = float(input("Digite o salario do comprador: "))
ano = int(input("Quantos anos a casa será paga? : "))

parcela = casa/ (ano * 12)

if parcela > salario * 0.3:
    print("Emprestimo negado")
else:
    print("Emprestimo aprovado")
    print("Voce pagará  R$ {} mensais, durante {} meses.".format(parcela,ano*12))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
