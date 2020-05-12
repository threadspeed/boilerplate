---
title: python script ARC4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ARC4'


## python ARC4

Python mysql example: ARC4

```python
from Crypto.Cipher import ARC4
obj1 = ARC4.new('01234567')
obj2 = ARC4.new('01234567')
text = 'abcdefghijklmnop'
cipher_text = obj1.encrypt(text)
cipher_text
obj2.decrypt(cipher_text)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
