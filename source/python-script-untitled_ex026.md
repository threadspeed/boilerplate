---
title: python script untitled ex026 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex026'


## python untitled ex026

Python example: untitled ex026

```python
num = int(input("Digite um número: "))
print("""Digite uma opção de conversão:
1- BINÁRIO
2- OCTAL
3- HEXADECIMAL""")
op = int(input("Escolha sua opção: "))

if op == 1:
    print("O valor convertido para BINÁRIO é {}".format(bin(num) [2:]))
elif op == 2:
    print("O valor convertido para OCTAL é {}".format(oct(num) [2:]))
elif op == 3:
    print("O valor convertido para HEXADECIMAL é {}".format(hex(num) [2:]))
else:
    print("Digite um número valido:")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
