---
title: python script ex059 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex059'


## python ex059

Python mysql example: ex059

```python
n1=int(input('Digite o primeiro valor: '))
n2=int(input('Digite o segundo valor: '))
p=0
lista=[]
lista.append(n1)
lista.append(n2)
print('[1]Somar [2]Multiplicar [3]Dividir [4]Maior Numero [5]Sair do programa')
p = int(input('Qual operacao voce quer fazer enter os numeros ? '))
while p in [0,1,2,3,4]:
    print('------------Opcoes-------------')
    print('[1]Somar [2]Multiplicar [3]Dividir [4]Maior Numero [5]Sair do programa')
    p = int(input('Qual operacao voce quer fazer enter os numeros ? '))
    if p == 1:
        soma=n1+n2
        print('A soma de {} e {} é igual a : {}'.format(n1,n2,soma))
    elif p == 2:
        mult=n1*n2
        print('A multiplicacao de {} e {} é igual a : {}'.format(n1, n2, mult))
    elif p == 3:
        div= n1/n2
        print('A divisao de {} e {} é igual a : {}'.format(n1, n2, div))
    elif p == 4:
        print('A o maior numero é : {}'.format(max(lista)))
    else:
        print('Essa opcao nao existe, tente novamente')
        p = int(input('qual operacao voce quer fazer enter os numeros ? '))
print('---FIM---')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
