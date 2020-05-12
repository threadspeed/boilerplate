---
title: python script wwcrypt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wwcrypt'

Functions in program: 
* `def decrypt(ciphertext, n):`

Modules used in program: 
* `import sys`
* `import getpass`
* `import base64`
* `import sys`
* `import random`
* `import math`
* `import getpass`
* `import base64`
* `import argparse`

## python wwcrypt

Python mysql example: wwcrypt

```python
#!/usr/bin/env python

from Crypto.Cipher import AES
from Crypto import Random
from struct import pack
import argparse
import base64
import getpass
import math
import random
import sys

OUTPUT_TEMPLATE = """#!/usr/bin/env python
from Crypto.Cipher import AES
import base64
import getpass
import sys


def decrypt(ciphertext, n):
    msg = base64.decodestring(ciphertext)
    iv, msg = msg[:16], msg[16:]
    key = getpass.getpass()
    while len(key) < 32:
        key += key
    key = key[:32]
    cipher = AES.new(key, AES.MODE_CBC, iv)
    sys.stdout.write(cipher.decrypt(msg)[:n])

decrypt(\"\"\"
{0}\"\"\", {1})
"""

parser = argparse.ArgumentParser()
parser.add_argument("-d", "--decrypt", help="decrypt instead of encrypting",
                    action="store_true")
parser.add_argument("-w", "--password", dest="bits",
                    help="generate password with bits of entropy")
parser.add_argument("-p", "--python", help="produce a Python script",
                    action="store_true")
parser.add_argument("-k", "--key", help="specify encryption key (not recommended)")
parser.add_argument("inputfile", nargs='?')
args = parser.parse_args()

if args.bits:
    chars = "abcdefghijklmnopqrstuvwxyz"
    chars += chars.upper()
    chars += "0123456789" + "~!@#$%^&*()+-=;:<>"
    pw_len = int(math.ceil(int(args.bits) * math.log(2) / math.log(len(chars))))
    print("Entropy: {0} bits".format(pw_len * math.log(len(chars)) / math.log(2)))
    print("".join([random.choice(chars) for i in range(pw_len)]))
    sys.exit(0)

inputfile = args.inputfile
inputtext = inputfile and open(inputfile).read() or sys.stdin.read()

key = args.key or getpass.getpass()
while len(key) < 32:
    key += key
key = key[:32]
iv = Random.new().read(16)
cipher = AES.new(key, AES.MODE_CBC, iv)

if args.decrypt:
    n = inputtext.split('\n')
    n, inputtext = int(n[0]), '\n'.join(n[1:])
    inputtext = base64.decodestring(inputtext)
    iv, msg = inputtext[:16], inputtext[16:]
    cipher = AES.new(key, AES.MODE_CBC, iv)
    sys.stdout.write(cipher.decrypt(msg)[:n])
    sys.exit(0)
else:
    n = len(inputtext)
    plen = 16 - (n & 15)
    padding = pack(plen * 'b', *(plen * [0]))
    msg = base64.encodestring(iv + cipher.encrypt(inputtext + padding))

if args.python:
    msg = OUTPUT_TEMPLATE.format(msg, n)
else:
    msg = '{0}\n'.format(n) + msg

sys.stdout.write(msg)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
