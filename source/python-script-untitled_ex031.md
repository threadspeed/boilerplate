---
title: python script untitled ex031 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex031'


## python untitled ex031

Python example: untitled ex031

```python
s1 = float(input("Digite o comprimento do primeiro segmento: "))
s2 = float(input("Digite o comprimento do segundo segmento: "))
s3 = float(input("Digite o comprimento do terceiro segmento: "))

if s1 < s2+s3  and s2 < s3+s1 and s3 < s1+s2:
    print("Os 3 segmentos formam um triângulo")

    if s1 == s2 and s2 == s3:
        print(("EQUILÁTERO"))
    elif (s1 == s2 and s2 != s3) or (s3 == s2 and s3 != s1) or (s3 == s1 and s2 != s3):
        print("ISÓSCELES")
    elif s1 != s2 and s1 != s3 and s3 != s2:
        print("ESCALENO")
else:
    print("Os 3 segmentos NÃO formam um triângulo")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
