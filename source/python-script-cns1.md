---
title: python script cns1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cns1'

Functions in program: 
* `def cipher(text, key):`

## python cns1

Python mysql example: cns1

```python
def cipher(text, key):
    result=""
    ptr=0
    for char in text:
        result = result + chr(int(char-32))

input_text = input("\nEnter text to encrypt:\t")
key = input("\nEnter encryption key:\t")

encryption = cipher(input_text, key)
print("\nEncrypted Cipher Text:\t" + encryption)
decryption = cipher(encryption, key)
print("\nDecrypted Cipher Text:\t" + decryption)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
