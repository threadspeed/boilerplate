---
title: python script untitled ex043 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex043'


## python untitled ex043

Python example: untitled ex043

```python
frase = str(input("Digite uma frase: ")).strip().upper()
palavras = frase.split()
inverso = ''
junto = ''.join(palavras)
for i in range(len(junto) - 1, -1, -1):
    inverso += junto[ i ]
if inverso == junto:
    print("Temos um polidromo")
else:
    print("Não é um polidromo")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
