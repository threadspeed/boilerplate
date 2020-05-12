---
title: python script ex37 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex37'


## python ex37

Python mysql example: ex37

```python
numero = int(input('Digite um numero'))
base= int(input('qual sera a base de conversao? 1->Binario: 2->Octal 3->Hexadecimal'))
if base == 1:
    print('O numero {} em binario é {}'.format(numero, bin(numero).replace('0b','')))
elif base == 2:
    print('o numero {} em octal é {}'.format(numero, oct(numero).replace('0o','')))
elif base == 3:
    print('O numero {} em Hexadecimal é {}'.format(numero, hex(numero).replace('0x','')))
else:
    print('Essa base nao pode ser calculada!')




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
