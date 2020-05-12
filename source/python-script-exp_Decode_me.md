---
title: python script exp Decode me (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exp Decode me'


Modules used in program: 
* `import base64`

## python exp Decode me

Python example: exp Decode me

```python
import base64

cipher = "D: mb xwhvxw mlnX 4X6AhPLAR4eupSRJ6FLt8AgE6JsLdBRxq57L8IeMyBRHp6IGsmgFIB5E :ztey xam lb lbaH"
cipher = cipher[::-1]
print(cipher)
decoded_cipher = ""

for i in range(len(cipher)):
    if cipher[i].isupper():
        val = ord(cipher[i]) + 12
        if val > ord('Z'):
            val = (val - ord('Z')) + ord('A') - 1
        decoded_cipher += chr(val)
    elif cipher[i].islower():
        val = ord(cipher[i]) + 7
        if val > ord('z'):
            val = (val - ord('z')) + ord('a') - 1
        decoded_cipher += chr(val)
    elif cipher[i].isdigit():
        val = ord('0') + ((int(cipher[i]) + 25) % 10)
        decoded_cipher += chr(val)
    else:
        decoded_cipher += cipher[i]
print(decoded_cipher)
# This is the flag: Q0NURntzSU1wTDNfYlU3X20xeDNkXzV1QnM3aXR1VDEwbl9DMXBoM1J9 Just decode it :P
decoded_cipher = base64.b64decode(decoded_cipher.split()[4])
print(decoded_cipher)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
