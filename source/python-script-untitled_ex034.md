---
title: python script untitled ex034 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex034'


Modules used in program: 
* `import random`

## python untitled ex034

Python example: untitled ex034

```python
import random

l = random.randint(1,3)

# CRIAÇÃO MENU
print("PEDRA / PAPEL / TESOURA")
print("1- PEDRA")
print("2- PAPEL")
print("3- TESOURA")
n = int(input("Qual sua jogada ? "))

itens = ["ERRO","PEDRA","PAPEL","TESOURA"]
if n >= 4 or n <= 0:
    print("Jogada Invalida")

else:
    print("_____________________________________")
    print("O Computador jogou {}" .format(itens[l]))
    print("O Jogador jogou {}" .format(itens[n]))
    print("_____________________________________")



    if l == n:
            print("EMPATE")
    elif l == 1:
        if n == 2:
            print("Jogador Venceu!")
        else:
            print("Computador Venceu!")
    elif l == 2:
        if n == 3:
            print("Jogador Venceu!")
        else:
            print("Computador Venceu!")
    else:
        if n == 1:
            print("Jogador Venceu!")
        else:
            print("Computador Venceu!")
print("_____________________________________")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
