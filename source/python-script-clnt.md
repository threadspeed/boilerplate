---
title: python script clnt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'clnt'

Functions in program: 
* `def pong(raw_data):`

Modules used in program: 
* `import urllib`
* `import base64`
* `import random`
* `import pyaes`

## python clnt

Python mysql example: clnt

```python
#!/usr/bin/python
import pyaes
import random
from hashlib import md5
import base64
import urllib

key="ruoski"
class ENCRYPTION:
	def __init__(self,key):
		# the salty sea salt made from the sea water on the seashore
		self.salt256 = "theseaissaltyb8ecbaacbd68de040cd78eb2ed5889130cceb4c49268ea4d506"
		self.aes = pyaes.AESModeOfOperationCTR(md5((self.salt256+key).encode()).hexdigest().encode("ascii"))
	def encrypt(self,data):
		return base64.b64encode(self.aes.encrypt(data))
	def decrypt(self,data):
		return self.aes.decrypt(base64.b64decode(data.encode()))

def pong(raw_data):
	data = urllib.quote(ENCRYPTION(key).encrypt(raw_data).decode())
	return ENCRYPTION(key).decrypt(urllib.urlopen("http://localhost:92/" + data).read()).decode()
	
while 1:
	raw_data = raw_input("Enter something cool >>> ")
	ping = pong(raw_data)
	
	#syn-ack
	if ping == raw_data:
		print("syn-ack")
		print(pong("Ok"))
	

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
