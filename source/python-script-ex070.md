---
title: python script ex070 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex070'


## python ex070

Python example: ex070

```python
listaNomes=[]
listaPreco=[]
p1000=0
total=0
while True:
    nome = str(input('Digite o Nome do Produto: ')).strip().upper()
    preco = input(f'Digite o valor do produto {nome}: ')
    while preco.isnumeric() == False:
        preco = input('O preco informado é incorreto, informe novamente:')
    preco=int(preco)
    listaNomes.append(nome) #adiciona nome na listaNomes
    listaPreco.append(preco) #adiciona Preco na listaPrecos
    if preco >= 1000:
        p1000 += 1
    total += preco
    barato = min(listaPreco) #pega o maior valor na lista de preco
    posicaoLista = listaPreco.index(barato) #pega o item que esta na mesma posicao que o Maior
    continuar=str(input('Quer continuar? [S/N]')).strip().upper()
    while continuar not in 'SN':
        continuar = str(input('Quer continuar? [S/N]')).strip().upper()
    if continuar == 'N':
        break
print(f'O total gasto é de R$ {total}.')
print(f'{p1000} produtos custam mais de  R$ 1000.00')
print(f'O produto mais barato foi {listaNomes[posicaoLista]} no valor de R${barato} ')




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
