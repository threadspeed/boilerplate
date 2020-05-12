---
title: python script srvr (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'srvr'


Modules used in program: 
* `import urllib`
* `import base64`
* `import random`
* `import pyaes`
* `import sys`
* `import ssl`

## python srvr

Python example: srvr

```python
#!/usr/bin/python
#usage: python srvr 92
from BaseHTTPServer import BaseHTTPRequestHandler,HTTPServer
import ssl
import sys
# -----------------------
import pyaes
import random
from hashlib import md5
import base64
import urllib

class ENCRYPTION:
	def __init__(self,key):
		# the salty sea salt made from the sea water on the seashore
		self.salt256 = "theseaissaltyb8ecbaacbd68de040cd78eb2ed5889130cceb4c49268ea4d506"
		self.aes = pyaes.AESModeOfOperationCTR(md5((self.salt256+key).encode()).hexdigest().encode("ascii"))
	def encrypt(self,data):
		return base64.b64encode(self.aes.encrypt(data))
	def decrypt(self,data):
		return self.aes.decrypt(base64.b64decode(data.encode()))

PORT_NUMBER = int(sys.argv[1])

#This class will handles any incoming request
class myHandler(BaseHTTPRequestHandler):
	#Handler for the GET requests
	def do_GET(self):
		key="barbie123"
		
		data = ENCRYPTION(key).decrypt(urllib.unquote(self.requestline.split()[1][1:]))
		print(data)
		
		self.send_response(200)
		self.end_headers()
		
		if data == "Ok":
			#connection established
			print("connection established")
			self.wfile.write(ENCRYPTION(key).encrypt("connection established").decode())
		else:
			print("Forward: " + ENCRYPTION(key).encrypt(data).decode())
			self.wfile.write(ENCRYPTION(key).encrypt(data).decode())
		return

try:
	#Create a web server and define the handler to manage the
	#incoming request
	server = HTTPServer(('', PORT_NUMBER), myHandler)
	#server.socket = ssl.wrap_socket(server.socket, certfile='cert.pem',keyfile='key.pem',  server_side=True)
	print('Started httpserver on port ' , PORT_NUMBER)
	
	#Wait forever for incoming htto requests
	server.serve_forever()
except:
	pass
finally:
	print('^C received, shutting down the web server')
	server.socket.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
