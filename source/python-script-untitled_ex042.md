---
title: python script untitled ex042 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex042'


## python untitled ex042

Python example: untitled ex042

```python
n = int(input("Digite um número: "))
primo = 0

if n > 0:
    for i in range(1, n+1):
        if n % i == 0:
            primo += 1
    if primo == 2:
        print("Este número é PRIMO")
    else:
        print("Este número NÃO é Primo")
else:
    for i in range(-1, n-1, -1):
        if n % i == 0:
            primo += 1
    if primo == 2:
        print("Este número é PRIMO")
    else:
        print("Este número NÃO é Primo")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
