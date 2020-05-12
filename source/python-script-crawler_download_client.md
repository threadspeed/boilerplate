---
title: python script crawler download client (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'crawler download client'


Modules used in program: 
* `import socket`

## python crawler download client

Python example: crawler download client

```python
#!/usr/bin/env python

import socket

print("Creating socket...",)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
print("done.")

port=51423

print("Connecting to remote host on port %d..." % port,)
s.connect(("127.0.0.1", port))
print("done.")


print("Connected from", s.getsockname())
print("Connected to", s.getpeername())

content = ""
try:
    send_len = s.send("http://www.toutiao.com/a6359107235901489409/")
    print(send_len)
    content = s.recv(4096000)
except :
    print("error")

print(content)
s.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
