---
title: python script encrypt file (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'encrypt file'

Functions in program: 
* `def decrypt_file(in_filename, out_filename, chunk_size, key, iv):`
* `def encrypt_file(in_filename, out_filename, chunk_size, key, iv):`

Modules used in program: 
* `import os`

## python encrypt file

Python example: encrypt file

```python
import os
from Crypto.Cipher import DES3

def encrypt_file(in_filename, out_filename, chunk_size, key, iv):
    des3 = DES3.new(key, DES3.MODE_CFB, iv)

    with open(in_filename, 'r') as in_file:
        with open(out_filename, 'w') as out_file:
            while True:
                chunk = in_file.read(chunk_size)
                if len(chunk) == 0:
                    break
                elif len(chunk) % 16 != 0:
                    chunk += ' ' * (16 - len(chunk) % 16)
                out_file.write(des3.encrypt(chunk))

def decrypt_file(in_filename, out_filename, chunk_size, key, iv):
    des3 = DES3.new(key, DES3.MODE_CFB, iv)

    with open(in_filename, 'r') as in_file:
        with open(out_filename, 'w') as out_file:
            while True:
                chunk = in_file.read(chunk_size)
                if len(chunk) == 0:
                    break
                out_file.write(des3.decrypt(chunk))
                
                
from Crypto import Random
iv = Random.get_random_bytes(8)
with open('to_enc.txt', 'r') as f:
    print('to_enc.txt: %s' % f.read())
encrypt_file('to_enc.txt', 'to_enc.enc', 8192, key, iv)
with open('to_enc.enc', 'r') as f:
    print('to_enc.enc: %s' % f.read())
decrypt_file('to_enc.enc', 'to_enc.dec', 8192, key, iv)
with open('to_enc.dec', 'r') as f:
    print('to_enc.dec: %s' % f.read())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
