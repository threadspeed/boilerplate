---
title: python script sacolas2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sacolas2'


Modules used in program: 
* `import random`

## python sacolas2

Python mysql example: sacolas2

```python
# !python3
'''
Post de https://groups.google.com/forum/#!topic/python-brasil/Cu_JkPSMebs

1) cada consumidor terá direito a até 2 sacolinhas por compra gratuitamente.

2) a partir da terceira sacolinha será cobrado um valor de R$ 0,08 por sacolinha.

Aqui eu considerei uma situação real que está acontecendo numa rede de supermercados de São Paulo:
O supermercado cobra R$ 0,08 + R$ 0,01 para as 2 primeiras sacolinhas e
depois dá um desconto de R$ 0,18 no final da compra. Ele faz isso para registrar as 2 sacolas.
Eu presenciei isso, mas não comprei 3 sacolas, portanto não sei como seriam registradas 3 sacolas,
mas podemos tentar prever isso no sistema.

Estou considerando que o consumidor sempre vai querer as 2 sacolas.
'''

import random

valor_compra = random.randint(1, 500)
valor_2_sacolas = 0.16
valor_especial = 0.02

desconto = valor_2_sacolas + valor_especial

print('Total: ' + str(valor_compra))
print('Desconto: ' + str(desconto))
print('A pagar: ' + str(valor_compra - desconto))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
