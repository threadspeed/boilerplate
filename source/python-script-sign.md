---
title: python script sign (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sign'


## python sign

Python mysql example: sign

```python
from Crypto.Hash import SHA256
from Crypto.PublicKey import RSA
from Crypto import Random
key = RSA.generate(1024, random_generator)
text = 'abcdefgh'
hash = SHA256.new(text).digest()
signature = key.sign(hash, '')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
