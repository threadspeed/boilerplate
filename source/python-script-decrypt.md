---
title: python script decrypt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'decrypt'


Modules used in program: 
* `import sys`
* `import uuid`
* `import random`
* `import base64`
* `import nacl.pwhash`
* `import nacl.utils`
* `import nacl.secret`
* `import simplecrypt`
* `import argparse`

## python decrypt

Python mysql example: decrypt

```python
import argparse
import simplecrypt
import nacl.secret
import nacl.utils
import nacl.pwhash
import base64
import random
import uuid
import sys

parser = argparse.ArgumentParser(description='encryption tool')
parser.add_argument('-p', '--password', help='your password (required)', required=True)
parser.add_argument('-f', '--filename', help='your file to encrypt', required=True)
parser.add_argument('-s', '--secret', help='your file that contains your secret', required=True)
args = parser.parse_args()

s = open(args.secret).read()
cipher = base64.b64decode(s)
try:
    pt = simplecrypt.decrypt(args.password, cipher)
except simplecrypt.DecryptionException:
    print("Error: Incorrect Passphrase to decrypt secret key")
    sys.exit(1)

password = base64.b64decode(pt.split(':')[0])
salt = base64.b64decode(pt.split(':')[1])

kdf = nacl.pwhash.argon2i.kdf
key = kdf(nacl.secret.SecretBox.KEY_SIZE, password, salt)

with open(args.filename, 'r') as x:
    file_data = x.read()
    decoded_data = base64.b64decode(file_data)

box = nacl.secret.SecretBox(key)
secret_msg = box.decrypt(decoded_data)
print(secret_msg)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
