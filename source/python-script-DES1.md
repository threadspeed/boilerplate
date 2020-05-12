---
title: python script DES1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'DES1'


## python DES1

Python mysql example: DES1

```python
from Crypto.Cipher import DES
from Crypto import Random
iv = Random.get_random_bytes(8)
des1 = DES.new('01234567', DES.MODE_CFB, iv)
des2 = DES.new('01234567', DES.MODE_CFB, iv)
text = 'abcdefghijklmnop'
cipher_text = des1.encrypt(text)
des2.decrypt(cipher_text)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
