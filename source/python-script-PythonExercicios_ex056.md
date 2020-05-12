---
title: python script PythonExercicios ex056 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex056'


## python PythonExercicios ex056

Python mysql example: PythonExercicios ex056

```python
somaIdade = 0
media_idade = 0
maiorIdadeHomem = 0
homemvelho = ''
menor = 0
for c in range(1, 5):
    print('{:-^25}'.format(' {}ª PESSOA '.format(c)))
    nome = str(input('Nome: ')).strip()
    idade = int(input('Idade: '))
    sexo = str(input('Digite o seu sexo [M/F]: ')).strip()
    somaIdade += idade
    if idade >= maiorIdadeHomem and sexo in 'Mm':
        maiorIdadeHomem = idade
        homemvelho = nome
    if sexo == 'f' and idade < 20:
        menor += 1
media_idade = somaIdade / 4
print('A média de idade do grupo é de {} anos'.format(media_idade))
print('O homem mais velho do grupo tem {} anos e o nome dele é {}'.format(maiorIdadeHomem, homemvelho))
print('Ao todo, {} mulher(es) tem menos de 20 anos no grupo.'.format(menor))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
