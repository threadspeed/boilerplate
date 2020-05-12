---
title: python script v3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'v3'

Functions in program: 
* `def add_number_to_list(number, prime_list):`
* `def is_number_prime(number):`
* `def get_random_limited_number(max_number):`

Modules used in program: 
* `import random`

## python v3

Python example: v3

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

    # Faltou checar se o número já está na lista, senão ele colocaria duas vezes.
    # Mas do jeito que tá ainda tá meio ruim, porque e como podemos melhorar?
    if is_number_prime(number) and number not in prime_list:
        add_number_to_list(number, prime_list)

print(f"Lista de primos: {prime_list}")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
