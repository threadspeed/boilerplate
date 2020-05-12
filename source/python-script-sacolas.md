---
title: python script sacolas (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sacolas'

Functions in program: 
* `def desconto_valor(valor_compra):`
* `def desconto_itens(itens_comprados):`
* `def valor_sacolas(sacolas):`

Modules used in program: 
* `import random`

## python sacolas

Python mysql example: sacolas

```python
# !python3
'''
Post de https://groups.google.com/forum/#!topic/python-brasil/Cu_JkPSMebs

1) cada consumidor terá direito a até 2 sacolinhas por compra gratuitamente.

2) a partir da terceira sacolinha será cobrado um valor de R$ 0,08 por sacolinha.

3) os consumidores que levarem sua própria sacola terão desconto acumulativo
de R$ 0,03 a cada 5 itens adquiridos, ou a cada compra no valor de R$ 30,00,
também acumulativo.
'''

import random
quer_sacolas = input('Você quer sacolas? (S) ou (N): ')


def valor_sacolas(sacolas):
    if sacolas > 2:
        return (sacolas - 2) * 0.08
    else:
        print('Digite um número maior que 2.')
        exit()


def desconto_itens(itens_comprados):
    if itens_comprados >= 5:
        return (itens_comprados // 5) * 0.03


def desconto_valor(valor_compra):
    if valor_compra >= 30:
        return (valor_compra // 30) * 0.03


if quer_sacolas == 'S' or quer_sacolas == 's':
    sacolas = int(input('Digite o número de sacolas: '))
    print('Valor pago por %i sacola(s) adicional(is): %.2f' %
          (sacolas - 2, valor_sacolas(sacolas)))
else:
    itens = random.randint(5, 50)
    ''' usei random simulando a quantidade de itens passados no caixa '''
    ''' vou usar randint simulando o valor da compra em inteiro '''
    valor_compra = random.randint(30, 500)
    if desconto_itens(itens) < desconto_valor(valor_compra):
        print('Desconto: %.2f' % desconto_itens(itens))
    else:
        print('Desconto: %.2f' % desconto_valor(valor_compra))


'''
Aqui eu considerei somente o que precisa ser informado no sistema.
Ou seja, o sistema não precisa saber se o cliente trouxe sacolas próprias.
Mas caso ele tenha trazido, o sistema irá calcular qual o menor desconto.
'''


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
