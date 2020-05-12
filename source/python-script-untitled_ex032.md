---
title: python script untitled ex032 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex032'


## python untitled ex032

Python mysql example: untitled ex032

```python
peso = float(input("Digite seu peso (KG): "))
altura = float(input("Digite sua altura (M): "))

imc = peso / (altura ** 2)

if imc < 18.5:
    print("Você está abaixo do peso. PROCURE UM NUTRICIONISTA !")
elif imc >= 18.5 and imc < 25:
    print("Você está no peso ideal. PARABÉNS! ")
elif imc >= 25 and imc < 30:
    print("Você está com sobre peso. CUIDADO!")
elif imc >= 30 and imc < 40:
    print("Você está com obesidade. PROCURE UM NUTRICIONISTA!")
else:
    print("Você está com obesidade mórbida. PROCURE UM NUTRICIONISTA URGENTE!")
print("Seu IMC é {:.1f}" .format(imc))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
