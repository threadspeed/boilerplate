---
title: python script PythonExercicios ex043 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex043'


Modules used in program: 
* `import time`

## python PythonExercicios ex043

Python mysql example: PythonExercicios ex043

```python
import time
print('=-=' * 15)
print('Calcule seu IMC - Índice de Massa Corporal')
print('=-=' * 15)
peso = float(input('Digite o seu peso: (Kg) '))
altura = float(input('Digite a sua altura: '))
imc = peso / (altura ** 2)
print('PROCESSANDO...')
time.sleep(2)
if imc < 18.5:
    print('Seu IMC é de {:.1f} portanto, você está ABAIXO DO PESO.'.format(imc))
elif imc < 25:
    print('Seu IMC é de {:.1f} portanto, você está com o PESO IDEAL. Parabéns!'.format(imc))
elif imc < 30:
    print('Seu IMC é de {:.1f} portanto, você está no SOBREPESO.'.format(imc))
elif imc < 40:
    print('Seu IMC é de {:.1f} portanto, você está na OBESIDADE'.format(imc))
else:
    print('Seu IMC é de {:.1f} portanto, você está na OBESIDADE MÓRBIDA.'.format(imc))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
