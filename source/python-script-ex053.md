---
title: python script ex053 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex053'


## python ex053

Python example: ex053

```python
frase= str(input('Digite uma frase: ')).strip().upper()
palavras=frase.split()
junto= ''.join(palavras)
inverso=''
for letra in range(len(junto)-1,-1,-1):
    inverso+=junto[letra]
if junto==inverso:
    print('A frase {} é um palindromo pois : {} é igual a {}'.format(frase,junto,inverso))
else:
    print('A frase {} nao é um palindromo pois : {} nao é igual a {}'.format(frase, junto, inverso))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
