---
title: python script PythonExercicios ex053 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex053'


## python PythonExercicios ex053

Python example: PythonExercicios ex053

```python
print('-=-' * 20)
print('{:^60}'.format('PYTHON - Palíndromo'))
print('-=-' * 20)
resultado = ''
frase = str(input('Digite uma frase para verificar se ela é um palíndromo: '))
for letra in frase:
    resultado = letra + resultado
print('O inverso de {} é {}'.format(frase.split()))
if frase.replace(' ', '').lower() == resultado.replace(' ', '').lower():
    print('Temos um palíndromo!')
else:
    print('A frase não é um palíndromo!')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
