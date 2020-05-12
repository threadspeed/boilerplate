---
title: python script RSAKey (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RSAKey'


Modules used in program: 
* `import base64`
* `import string`
* `import random`

## python RSAKey

Python mysql example: RSAKey

```python
#coded by Amin Beirami---> beirami.m.a@gmail.com
from Crypto.PublicKey import RSA
from Crypto import Random
from Crypto.Signature import PKCS1_v1_5
from Crypto.Hash import SHA256
import random
import string
import base64

class RSAEncryption():

	def generate_keys(self):
		random_generator = Random.new().read
		key = RSA.generate(1024,random_generator)
		privateKey = key.exportKey()
		publicKey = key.publickey().exportKey()
		return publicKey, privateKey

	def encryption(self,message):
        publicKey = open(public_key_doc, "r").read() #my public key is saved in the file with the name public_key_doc
		publicKeyObject = RSA.importKey(publicKey)
		randomParameter = random.choice(string.ascii_uppercase)
		encryptedMessage = publicKeyObject.encrypt(message.encode('utf-8'),randomParameter)[0]
		encodedEncryptedMessage = base64.b64encode(encryptedMessage)
		return encodedEncryptedMessage

	def decryption(self,encodedMessage):
        privateKey = open(private_key_doc, "r").read()
		privateKeyObject = RSA.importKey(privateKey)
		decodedMessage = base64.b64decode(encodedMessage)
		decryptedMessage = privateKeyObject.decrypt(decodedMessage)
		return decryptedMessage

	def generate_signature(self, message):
        privateKey = open(private_key_doc, "r").read() #my private key is saved in the file with the name private_key_doc
		privateKeyObject = RSA.importKey(privateKey)
		hashedMessage = SHA256.new()
		hashedMessage.update(message)
		signer = PKCS1_v1_5.new(privateKeyObject)
		signature = signer.sign(hashedMessage)
		encodedSignature = base64.b64encode(signature)
		return encodedSignature

	def verifying_signature (self, message, signature):
        publicKey = open(public_key_doc, "r").read()
		publicKeyObject = RSA.importKey(publicKey)
		hashedMessage = SHA256.new()
		hashedMessage.update(message)
		decodedSignature = base64.b64decode(signature)
		verifier = PKCS1_v1_5.new(publicKeyObject)
		autheticate = verifier.verify(hashedMessage,decodedSignature)
		if autheticate:
			return 'Trusted'
		else:
			return 'Untrusted'

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
