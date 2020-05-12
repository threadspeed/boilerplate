---
title: python script AESCBC (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'AESCBC'

Functions in program: 
* `def pad(plain_text):`

Modules used in program: 
* `import random`
* `import base64`

## python AESCBC

Python example: AESCBC

```python
from Crypto.Cipher import AES
from Crypto import Random
import base64
import random

block_size = AES.block_size


#unpad = lambda s : s[0:-ord(s[-1])]

def pad(plain_text):
    """
    func to pad cleartext to be multiples of 8-byte blocks.
    If you want to encrypt a text message that is not multiples of 8-byte blocks, 
    the text message must be padded with additional bytes to make the text message to be multiples of 8-byte blocks.
    """
    number_of_bytes_to_pad = block_size - len(plain_text) % block_size
    ascii_string = chr(number_of_bytes_to_pad)
    padding_str = number_of_bytes_to_pad * ascii_string
    padded_plain_text =  plain_text + padding_str
    return padded_plain_text


key='sixteencharacter'
plain='secret message of any length'
plain = pad(plain)

iv = 'jvHJ1XFt0IXBrxxx'

cipher = AES.new(key, AES.MODE_CBC, iv)
encrypted_bytes = cipher.encrypt(plain)

encrypted_text = base64.urlsafe_b64encode(encrypted_bytes).decode("utf-8")

print('Encrypted Text: ' + encrypted_text)

# Output
# Encrypted Text: gnLjDGBLvO3-SUu56-FPRDA33Wx-XNoqcoygdyjG3TD1W8NJOtXZPmm76JRJ36QI

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
