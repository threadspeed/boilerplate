---
title: python script check apssword (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'check apssword'

Functions in program: 
* `def check_password(clear_password, password_hash):`

## python check apssword

Python mysql example: check apssword

```python
from Crypto.Hash import SHA256
def check_password(clear_password, password_hash):
    return SHA256.new(clear_password).hexdigest() == password_hash


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
