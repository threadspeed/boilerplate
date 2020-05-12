---
title: python script DES (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'DES'


## python DES

Python example: DES

```python
from Crypto.Cipher import DES
des = DES.new('01234567', DES.MODE_ECB)
text = 'abcdefgh'
cipher_text = des.encrypt(text)
des.decrypt(cipher_text)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
