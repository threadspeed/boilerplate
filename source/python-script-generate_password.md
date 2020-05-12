---
title: python script generate password (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generate password'

Functions in program: 
* `def generate_password(pass_length):`

Modules used in program: 
* `import random`

## python generate password

Python example: generate password

```python
from string import punctuation, ascii_letters, digits
import random

def generate_password(pass_length):
    symbols = ascii_letters + digits + punctuation
    secure_random = random.SystemRandom()
    password = "".join(secure_random.choice(symbols) for i in range(pass_length))
    return password

generate_password(15)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
