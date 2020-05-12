---
title: python script untitled ex045 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex045'


## python untitled ex045

Python example: untitled ex045

```python

for i in range(1,6):
    peso = float(input("Digite o peso da {} pessoa: ".format(i)))
    if i == 1:
        menor = peso
        maior = peso
    #--- EVITAR ERROS ----#
    if peso > maior:
        maior = peso
    if peso < menor:
        menor = peso
print("O maior peso é {} KG e o menor peso é {} KG.".format(maior,menor))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
