---
title: python script ex056 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex056'


## python ex056

Python mysql example: ex056

```python
nomes = [] # Armazena os nomes das pessoas
idades = [] # Armazena as idades das pessoas
sexos = [] # Armazena os sexos das pessoas
soma = 0 # Soma as idades das pessoas
maisVelho = 0 # Armazena a idade do homem mais velho
nomeM = '' # Concatena nome e idade do homem mais velho
mSub20 = 0 # Armazena a quantidade de mulheres com idades abaixo de 20 anos
nomeF = '' # Concatena nome e idade das mulheres abaixo de 20 anos
for i in range(0, 4):
    print(str(i+1) + 'ª' + ' pessoa: ')
    nomes.append(input('Nome: ').capitalize())
    idades.append(int(input('Idade: ')))
    sexos.append(input('Sexo(M/F): ').upper())
    soma += idades[i]
    if sexos[i] == 'F' and idades[i] < 20:
        nomeF += nomes[i] + ',' + str(idades[i]) + ' anos; '
        mSub20 += 1
for i in range(0, len(idades)):
    if sexos[i] == 'M' and idades[i] > maisVelho:
        maisVelho = idades[i]
        nomeM = nomes[i]
print('Média de idade do grupo: {:.2f} anos.'.format(soma/4))
print('Homem mais velho: {}, {} anos.'.format(nomeM, maisVelho))
print('Mulheres acima de 20 anos: {}. {}'.format(mSub20, nomeF))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
