---
title: python script ex069 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex069'


## python ex069

Python mysql example: ex069

```python
idades = []
sexos = []
listageral= []
idades18=0
homens=0
mulheres=0
resposta = 'S'
while resposta == 'S':
    idade = int(input('Digite a Idade :'))
    idades.append(idade)
    if idade > 18:
        idades18 +=1
    sexo = str(input('Digite o Sexo: [M/F]')).upper()
    while sexo not in 'MF':
        print('Voce digitou um valor invalido, tente novamente!')
        sexo = str(input('Digite o Sexo: [M/F]')).upper()
    sexos.append(sexo)
    if sexo == 'M':
        homens+=1
    if sexo == 'F' and idade < 20:
        mulheres+=1
    resposta = str(input('Quer Continuar? [S/N]')).upper()
    while resposta not in 'SN':
        print('Voce digitou um valor invalido, tente novamente!')
        resposta= str(input('Quer Continuar? [S/N]')).upper()
    if resposta == 'N':
        break

print(f'Existem {idades18} pessoas com mais de 18 anos.')
print(f'Foram encontrados {homens} Homens no seu cadastro')
print(f'Foram encontrados {mulheres} mulheres com menos de 20 anos no seu cadastro')
print('FIM')




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
