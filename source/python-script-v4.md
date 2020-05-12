---
title: python script v4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'v4'

Functions in program: 
* `def add_number_to_list(number, prime_list):`
* `def is_number_prime(number):`
* `def get_random_limited_number(max_number):`

Modules used in program: 
* `import random`

## python v4

Python mysql example: v4

```python
import random

def get_random_limited_number(max_number):
    return random.randint(2, max_number)

def is_number_prime(number):
    for test in range(2, number):
        if number % test == 0:
            return False

    return True

def add_number_to_list(number, prime_list):
    prime_list.append(number)

prime_list = []
qty = int(input('Insira a quantidade: '))
max_number = int(input('Insira o maior número possível: '))

while len(prime_list) < qty:
    number = get_random_limited_number(max_number)

    # is_number_prime é uma operação relativamente custosa
    # como estava na v3, ele calculava se o número era primo e só depois ele checava se já estava na lista
    # neste código, o problema vai embora, porque a checagem é feita antes, e ele não vai calcular de novo se
    #  o número já estiver na lista
    if number in prime_list:
        continue

    if is_number_prime(number):
        add_number_to_list(number, prime_list)

print(f"Lista de primos: {prime_list}")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
