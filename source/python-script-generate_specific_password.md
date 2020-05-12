---
title: python script generate specific password (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generate specific password'

Functions in program: 
* `def generate_specific_password(pass_length):`

Modules used in program: 
* `import random`

## python generate specific password

Python example: generate specific password

```python
from string import ascii_letters, digits
import random

def generate_specific_password(pass_length):
    """
    Generates an alphanumeric password with at least one lowercase character, 
    at least one uppercase character and at least three digits 
    """
    alphabet = ascii_letters + digits
    secure_random = random.SystemRandom()
    while True:
        password = ''.join(secure_random.choice(alphabet) for i in range(pass_length))
        if (any(c.islower() for c in password)
           and any(c.isupper() for c in password)
           and sum(c.isdigit() for c in password) >= 3):
            break
    return password

generate_specific_password(5)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
