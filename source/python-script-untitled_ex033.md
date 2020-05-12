---
title: python script untitled ex033 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex033'


## python untitled ex033

Python mysql example: untitled ex033

```python
valor = float(input("Digite o valor do produto: R$ "))

# CRIAÇÃO MENU
print("METODOS DE PAGAMENTO")
print("1- Á VISTA no Dinheiro/Cheque")
print("2- Á VISTA no Cartão")
print("3- PARCELADO")
n = int(input("Digite o método de pagamento:"))
# LOGICA MENU
if n == 1:
    final = valor * 0.9
elif n == 2:
    final = valor * 0.95
elif n == 3:
    parcelas = int(input("Digite o número de parcelas: "))
    if parcelas <= 2:
        final = valor
    else:
        final = valor * parcelas * 1.3
    print("Você pagará em {} parcelas no valor de R$ {:.2f}".format(parcelas, final / parcelas))
else:
    print("Não há está opção")
    final = valor
print("O valor final do produto é R$ {:.2f}".format(final))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
