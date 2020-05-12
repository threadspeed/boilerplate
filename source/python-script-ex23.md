---
title: python script ex23 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex23'


## python ex23

Python example: ex23

```python
num: int= int(input('Digite um  numero entre 0 e 9999: '))
    
while num > 9999:
      num=int(input('Esse numero nao é valido, digite novamente:'))
num=str(num)
x= len(num)

print('Unidade é:{}'.format(num[x-1]))
print('Dezena é: {}'.format(num[x-2]))
print('Centena é: {}'.format(num[x-3]))
print('O Milhar é: {}'.format(num[x-4]))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
