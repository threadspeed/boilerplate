---
title: python script PythonExercicios ex045%2520JOKENPO (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex045%2520JOKENPO'


Modules used in program: 
* `import emoji`
* `import random`

## python PythonExercicios ex045%2520JOKENPO

Python example: PythonExercicios ex045%2520JOKENPO

```python
from time import sleep
import random
import emoji
jokenpo = ['', 'Pedra', 'Papel', 'Tesoura']
pc = random.randint(1,3)
print('JOKENPÔ')
print('Escolha Pedra, Papel ou Tesoura e tente vencer o COMPUTADOR =)')
print(emoji.emojize('[ 1 ] = PEDRA :punch: \n[ 2 ] - PAPEL :hand: \n[ 3 ] - TESOURA :v: \n[ 4 ] - REGRAS :book:', use_aliases=True))
jogador = int(input('Faça sua escolha: '))
print('JO')
sleep(1)
print('KEN')
sleep(1)
print('PO!!!')
if jogador == pc:
    print('-=-' * 10)
    print('O computador escolheu {}'.format(jokenpo[pc]))
    print('O jogador escolheu {}'.format(jokenpo[jogador]))
    print('-=-' * 10)
    print('EMPATE, tente novamente!')
elif jogador == 1 and pc == 2 or jogador == 2 and pc == 3 or jogador == 3 and pc == 1:
    print('-=-' * 10)
    print('O computador escolheu {}'.format(jokenpo[pc]))
    print('O jogador escolheu {}'.format(jokenpo[jogador]))
    print('-=-' * 10)
    print('O Computador Venceu!'.format(jokenpo[pc]))
elif jogador == 4:
    print('''Pedra ganha da tesoura (amassando-a ou quebrando-a).
Tesoura ganha do papel (cortando-o).
Papel ganha da pedra (embrulhando-a).''')
elif jogador <= 0 or jogador >= 5:
    print('Opção inválida. Tente novamente!')
else:
    print('-=-' * 10)
    print('O computador escolheu {}'.format(jokenpo[pc]))
    print('O jogador escolheu {}'.format(jokenpo[jogador]))
    print('-=-' * 10)
    print('Você venceu, Parabéns!'.format(jokenpo[pc]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
