---
title: python script v2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'v2'

Functions in program: 
* `def add_number_to_list(number, prime_list):`
* `def is_number_prime(number):`
* `def get_random_limited_number(max_number):`

Modules used in program: 
* `import random`

## python v2

Python mysql example: v2

```python
import random

# Tem um erro nesse código, consegue descobrir qual é?
# Não é bem um erro, mas ele tá fazendo algo que você provavelmente não tá esperando
# Solução na v3

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

    if is_number_prime(number):
        add_number_to_list(number, prime_list)

print(f"Lista de primos: {prime_list}")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
