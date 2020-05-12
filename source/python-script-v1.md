---
title: python script v1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'v1'


Modules used in program: 
* `import random`

## python v1

Python example: v1

```python
import random

# Tem um erro nesse código, consegue descobrir qual é?
# Não é bem um erro, mas ele tá fazendo algo que você provavelmente não tá esperando
# Solução na v3

prime_list = []
qty = int(input('Insira a quantidade: '))
max_number = int(input('Insira o maior número possível: '))

while len(prime_list) < qty:
    number = random.randint(2, max_number)

    # Assume que o numero é primo
    is_prime = True
    for test in range(2, number):
        print(f"{test}, {number}")
        if number % test == 0:
            is_prime = False

    if not is_prime:
      continue

    # Se chegou até aqui, é porque é primo
    prime_list.append(number)

print(f"Lista de primos: {prime_list}")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
