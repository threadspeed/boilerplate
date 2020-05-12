---
title: python script aes url (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'aes url'

Functions in program: 
* `def url_to_str(s):`
* `def str_to_url(s):`
* `def get_aes():`
* `def unbuffer_str(b):`
* `def buffer_str(s):`

Modules used in program: 
* `import random`
* `import string`

## python aes url

Python mysql example: aes url

```python
#!/usr/bin/env python3

# this code is all wrong; don't use it.
# constant IV + allowing a plaintext attack means that this is totally broken.
# the intention was to be able to store javascript code in URLs and then run it.
# but that problem needs authentication, not encryption.
# so, just add an HMAC's 128-bit digest to the URL.

import string
import random
from Crypto import Random
from Crypto.Cipher import AES
from base64 import urlsafe_b64encode, urlsafe_b64decode

key = Random.new().read(32) # store/hardcode this key

def buffer_str(s):
    s = s.encode()
    s = Random.new().read(16) + s
    s += b' '*(15-( (len(s)-1) %16))
    assert 0 == len(s) % 16
    return s

def unbuffer_str(b):
    return b[16:].decode().rstrip()

def get_aes():
    return AES.new(key, AES.MODE_CBC, b' '*16)  #constant IV requires initial 16 random bytes for ideal security.  4 would be sufficient, though.

def str_to_url(s):
    return urlsafe_b64encode(get_aes().encrypt(buffer_str(s)))
def url_to_str(s):
    return unbuffer_str(get_aes().decrypt(urlsafe_b64decode(s)))


message = ''.join(random.choice(string.printable[:-5]) for _ in range(random.randint(0,180)))
print(len(message), '\t', message)
url = str_to_url(message)
print(len(url), '\t', url)
assert url_to_str(url) == message.rstrip()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
