---
title: python script cks (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cks'

Functions in program: 
* `def verify(message, signature, pub_key):`
* `def sign(message, priv_key):`
* `def decrypt(ciphertext, priv_key):`
* `def encrypt(message, pub_key):`
* `def getpublickey(priv_key):`
* `def importKey(externKey):`
* `def newkeys(keysize):`

## python cks

Python example: cks

```python
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP
from Crypto.Signature import PKCS1_v1_5
from Crypto.Hash import SHA512, SHA384, SHA256, SHA, MD5
from Crypto import Random
from base64 import b64encode, b64decode

def newkeys(keysize):
    random_generator = Random.new().read
    key = RSA.generate(keysize, random_generator)
    private, public = key, key.publickey()
    return public, private

def importKey(externKey):
    return RSA.importKey(externKey)

def getpublickey(priv_key):
    return priv_key.publickey()

def encrypt(message, pub_key):
    #RSA encryption protocol according to PKCS#1 OAEP
    cipher = PKCS1_OAEP.new(pub_key)
    return cipher.encrypt(message)

def decrypt(ciphertext, priv_key):
    #RSA encryption protocol according to PKCS#1 OAEP
    cipher = PKCS1_OAEP.new(priv_key)
    return cipher.decrypt(ciphertext)

def sign(message, priv_key):
    signer = PKCS1_v1_5.new(priv_key)
    digest = SHA.new()
    digest.update(message)
    return signer.sign(digest)

def verify(message, signature, pub_key):
    signer = PKCS1_v1_5.new(pub_key)
    digest = SHA.new()
    digest.update(message)
    return signer.verify(digest, signature)


msg1 = "Hello Ton"

keysize = 2048
(public, private) = newkeys(keysize)
encrypted = b64encode(encrypt(msg1, public))
decrypted = decrypt(b64decode(encrypted), private)
signature = b64encode(sign(msg1, private))
verify2 = verify('Hello Ton', b64decode(signature), public)

# print(private.exportKey('PEM'))
# print(public.exportKey('PEM'))
# print("Encrypted: " + encrypted)
# print("Decrypted: '%s'" % decrypted)
# print("Signature: " + signature)
# print("Verify: %s" % verify)

print("Verify: %s" % verify2)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
