---
title: python script RSA (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RSA'


Modules used in program: 
* `import Crypto`
* `import ast`

## python RSA

Python example: RSA

```python
# -*- coding: utf-8 -*-
import ast
import Crypto
from Crypto.PublicKey import RSA
from Crypto import Random

# random_generator = Random.new().read
# key = RSA.generate(1024, random_generator)


# publickey = key.publickey()

# encrypted = publickey.encrypt('encrypt this message', 32)
# print(encrypted)

# decrypted = key.decrypt(encrypted)

# print(decrypted)

class RSASelf:
	def __init__(self):
		self.key = RSA.generate(1024, Random.new().read)
		self.publickey = self.key.publickey()

	def encrypt(self, text):
		return self.publickey.encrypt(text, 32)

	def decrypt(self, encryptedText):
		return self.key.decrypt(encryptedText)

	def export(self):
		return self.key.exportKey('PEM')
rsa = RSASelf()
enc =  rsa.encrypt('hello world RSA')
print(enc)

dec = rsa.decrypt(ast.literal_eval(str(enc)))
print(dec)

print(rsa.export())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
