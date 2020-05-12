---
title: python script Exercicios08 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Exercicios08'


## python Exercicios08

Python example: Exercicios08

```python
from math import trunc

'''print('====== DESAFIO 01 ======')'''
#crie um programa que leia um numero real na tela e mostre sua porção inteira
#Médoto com importação
'''num = float(input('Qual o número desejado? '))
print('A porção inteira de {} é {}'.format(num, trunc(num)))'''
#Método sem importação
'''num = float(input('Digite um numero'))
print('A porção inteira de {} é {}'.format(num, int(num)))'''

'''print('====== DESAFIO 02 ======')'''
#CALCULO DE HIPOTENUSA

#Método sem importação
'''co = float(input('Comprimento do cateto oposto: '))
ca = float(input('Comprimento do cateto adjacente: '))
hi = (ca ** 2 + co ** 2) ** (1/2)
print('A hipotenusa vai medir {:.2f}'.format(hi))'''

#Método com importação
'''import math
co = float(input('Comprimento do cateto oposto: '))
ca = float(input('Comprimento do cateto adjacente'))
hi = math.hypot(co,ca)
print('A hipotenusa vai medir {:.2f}'.format(hi))'''

'''import math
angulo = float(input('Digite o angulo que você deseja'))
seno = math.sin(math.radians(angulo))
cosseno = math.cos(math.radians(angulo))
tangente = math.tan(math.radians(angulo))
print('O angulo de {}° tem o SENO de {:.2f}, o COSSENO de {:.2f} e a TANGENTE de {:.2f}'.format(angulo,seno,cosseno,tangente))
'''
'''import random
n1 =  str(input('Primeiro aluno:'))
n2 = str(input('Segundo aluno: '))
n3 = str(input('Terceiro aluno:'))
n4 = str(input('Quarto aluno: '))
lista =[n1,n2,n3,n4]
escolhido = random.choice(lista)
print('O aluno selecionado para apagar o quadro foi {}'.format(escolhido))
'''
'''import random
n1 =  str(input('Primeiro aluno:'))
n2 = str(input('Segundo aluno: '))
n3 = str(input('Terceiro aluno:'))
n4 = str(input('Quarto aluno: '))
lista = [n1,n2,n3,n4]
random.shuffle(lista)
print('A ordem para apagar o quadro é : ')
print(lista)'''

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
