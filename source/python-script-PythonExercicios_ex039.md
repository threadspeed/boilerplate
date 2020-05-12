---
title: python script PythonExercicios ex039 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex039'


## python PythonExercicios ex039

Python mysql example: PythonExercicios ex039

```python
from datetime import date
sexo = input('Digite seu sexo: ').lower()
if sexo == 'masculino':
    ano = int(input('Digite o ano do seu nascimento: '))
    hoje = date.today().year
    if hoje - ano == 18:
        print('Você tem {} anos. Chegou o grande dia. HORA DE SE ALISTAR!'.format(hoje - ano))
    elif hoje - ano > 18:
        print('Você tem {} anos e já passou {} ano(s) do seu '
              'alistamento que foi em {}. Se ainda não se alistou, aliste-se!'.format(hoje - ano, hoje - ano - 18, hoje - (hoje - ano - 18)))
    else:
        print('Ainda falta {} ano(s) para você se alistar. Você deve se alistar em {}. Fique atento!'.format(18 - (hoje - ano), hoje + 18 - (hoje - ano)))
elif sexo == 'feminino':
    print('Você é do sexo Feminino, portanto, não precisa se alistar!')
else:
    print('Sexo indefinido.')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
