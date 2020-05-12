---
title: python script untitled ex046 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex046'


## python untitled ex046

Python example: untitled ex046

```python
j = 0
maior = 0
media = 0

for i in range(1,5):
    print("-=-=-=-=-=-=-=  {}ª PESSOA -=-=-=-=-=-=-= ".format(i))
    nome = str(input("NOME: "))
    idade = int(input("IDADE: "))
    media += idade
    sexo = str(input("SEXO [M/F]: ")).strip().upper()
    if  sexo == "M" or "F":
        if sexo == "M":
            if i==1:
                maior = idade
            elif idade >= maior:
              maior = idade
        elif sexo== "F" and idade >= 20:
            j += 1
    else:
        print("SEXO INVALIDO")

print("São {} mulheres acima dos 20 anos".format(j))
print("O Homem mais velho tem {} anos.".format(maior))
print("A média de idade do grupo é {} anos." .format(media/4))




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
