---
title: python script ex071 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex071'


## python ex071

Python example: ex071

```python
print('='*21)
print('    Banco-Ziegler    ')
print('='*21)
valor = input('Qual o valor do saque: ')
while valor.isnumeric() == False:
    valor = input('Este valor nao é válido, digite outro valor do saque: ')
valor=int(valor)
nota50 = (int(valor))/50
print(f'Total de {int(nota50)} notas de R$50 ')
resto = valor - (int(nota50))*50
if resto>0:
    nota20 = int(resto) /20
    print(f'Total de {int(nota20)} notas de R$20 ')
    resto = resto - (int(nota20))*20
    if resto>0:
        nota10 = int(resto) /10
        print(f'Total de {int(nota10)} notas de R$10 ')
        resto = resto - (int(nota10))*10
        if resto > 0:
            nota1 = int(resto) /1
            print(f'Total de {int(nota1)} notas de R$1 ')
print('='*21,'FIM','='*21)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
