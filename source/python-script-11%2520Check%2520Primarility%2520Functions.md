---
title: python script 11%2520Check%2520Primarility%2520Functions (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '11%2520Check%2520Primarility%2520Functions'

Functions in program: 
* `def is_prime(number):`
* `def get_integer():`

## python 11%2520Check%2520Primarility%2520Functions

Python mysql example: 11%2520Check%2520Primarility%2520Functions

```python
def get_integer():
    return int(input('Enter a number: '))

def is_prime(number):
    if number > 1:
        if number == 2:
            return True
        for i in range(2, number):
            if (number % i) == 0:
                return False
            else:
                return True
    else:
        return False

user = get_integer()
if is_prime(user):
    print('The number is a prime number')
else:
    print('The number is not a prime number')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
