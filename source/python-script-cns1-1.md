---
title: python script cns1-1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cns1-1'

Functions in program: 
* `def cipher(text, key):`

## python cns1-1

Python mysql example: cns1-1

```python
def cipher(text, key):
      result = ""
      ptr = 0
      for i in range(len(text)):
            x = chr((ord(text[i])-ord('a')+ord(key[i%len(key)])-ord('a'))%26)
            x+=chr(ord('A'))
            result+=x
      return result
                      

 

input_text = input("\nEnter Text To Encrypt:\t")
encryption_key = input("\nEnter encryption key:\t")
encryption = cipher(input_text, encryption_key)
print("\nEncrypted Cipher Text:\t" + encryption)
#decryption = cipher(encryption, encryption_key)
#print("\nDecrypted Vernam Cipher Text:\t" + decryption)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
