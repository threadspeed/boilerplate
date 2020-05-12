---
title: python script decode (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'decode'

Functions in program: 
* `def decode(inp):`
* `def encode(inp):`

Modules used in program: 
* `import base64`
* `import random`
* `import base64`
* `import random`

## python decode

Python example: decode

```python
#!/usr/bin/env python3

"""
encode.pyc is a compiled python file. 
The first 2 bytes \x16\x0d == 3350 mean that it's a python3 file. 
Python3.4 throws a bad magic number error, but python3.5 works. 
After trying a couple python decompilers, I found that unpyc3 worked the best:
```
duck@computer:~/Downloads$ python3.5 ../unpyc3.py encode.pyc 
import random
import base64
P = [27, 35, 50, 11, 8, 20, 44, 30, 6, 1, 5, 2, 33, 16, 36, 64, 3, 61, 54, 25, 12, 21, 26, 10, 57, 53, 38, 56, 58, 37, 43, 17, 42, 47, 4, 14, 7, 46, 34, 19, 23, 40, 63, 18, 45, 60, 13, 15, 22, 9, 62, 51, 32, 55, 29, 24, 41, 39, 49, 52, 48, 28, 31, 59]
S = [68, 172, 225, 210, 148, 172, 72, 38, 208, 227, 0, 240, 193, 67, 122, 108, 252, 57, 174, 197, 83, 236, 16, 226, 133, 94, 104, 228, 135, 251, 150, 52, 85, 56, 174, 105, 215, 251, 111, 77, 44, 116, 128, 196, 43, 210, 214, 203, 109, 65, 157, 222, 93, 74, 209, 50, 11, 172, 247, 111, 80, 143, 70, 89]
inp = input()
inp += ''.join(chr(random.randint(0, 47)) for _ in range(64 - len(inp) % 64))
ans = ['' for i in range(len(inp))]
for j in range(0, len(inp), 64):
    for i in range(64):
        ans[j + P[i] - 1] = chr((ord(inp[j + i]) + S[i]) % 256)
ans = ''.join(ans)
print(base64.b64encode(ans.encode('utf8')).decode('utf8'))
```

I've modified the encode into a function and created its accompanying decode function.

Note: because the length of the cleartext isn't stored anywhere in the cipher text, 
the deciphered text will have a few garbage characters at the end. 
This doesn't matter to us because we can just eyeball the flag from the jibberish.
"""

import random
import base64
P = [27, 35, 50, 11, 8, 20, 44, 30, 6, 1, 5, 2, 33, 16, 36, 64, 3, 61, 54, 25, 12, 21, 26, 10, 57, 53, 38, 56, 58, 37, 43, 17, 42, 47, 4, 14, 7, 46, 34, 19, 23, 40, 63, 18, 45, 60, 13, 15, 22, 9, 62, 51, 32, 55, 29, 24, 41, 39, 49, 52, 48, 28, 31, 59]
S = [68, 172, 225, 210, 148, 172, 72, 38, 208, 227, 0, 240, 193, 67, 122, 108, 252, 57, 174, 197, 83, 236, 16, 226, 133, 94, 104, 228, 135, 251, 150, 52, 85, 56, 174, 105, 215, 251, 111, 77, 44, 116, 128, 196, 43, 210, 214, 203, 109, 65, 157, 222, 93, 74, 209, 50, 11, 172, 247, 111, 80, 143, 70, 89]

def encode(inp):
    # Padd inp with random characters for a length divisible by 64
    inp += ''.join(chr(random.randint(0, 47)) for _ in range(64 - len(inp) % 64))
    # ans will hold our encoded text
    ans = ['' for i in range(len(inp))]
    # For each block of 64 characters
    for j in range(0, len(inp), 64):
        # Iterate through each character in the block
        for i in range(64):
            # Two things happen here: First, the S list is used to shift individual characters
            # Second: the P list is used to mix/shuffle the characters in a block
            ans[j + P[i] - 1] = chr((ord(inp[j + i]) + S[i]) % 256)
    ans = ''.join(ans)
    return base64.b64encode(ans.encode('utf8')).decode('utf8')

def decode(inp):
    # The decode operation is very similar to the encode operation
    inp = base64.b64decode(inp.encode("utf8")).decode("utf8")
    # print(inp)
    ans = ['' for i in range(len(inp))]
    for j in range(0, len(inp), 64):
        for i in range(64):
            # swap input and output indices for the mixing/shuffling
            oind = j + P[i] - 1
            iind = j + i
            # subtract S offsets instead of adding
            # I add the extra 256 because sometimes modulo of negative numbers isn't nicely defined in languages, but it shouldn't be needed in Python 
            ans[iind] = chr((ord(inp[oind]) - S[i] + 256) % 256)
    ans = ''.join(ans)
    return ans


if __name__ == '__main__':
    # enc = encode("hello, world")
    # print(enc)
    dec = decode("Wmkvw680HDzDqMK6UBXChDXCtC7CosKmw7R9w7JLwr/CoT44UcKNwp7DllpPwo3DtsOID8OPTcOWwrzDpi3CtMOKw4PColrCpXUYRhXChMK9w6PDhxfDicOdwoAgwpgNw5/Cvw==")
    print(dec)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
