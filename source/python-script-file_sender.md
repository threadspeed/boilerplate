---
title: python script file sender (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'file sender'


Modules used in program: 
* `import socket`

## python file sender

Python mysql example: file sender

```python
import socket

client = socket.socket()

client.connect(("127.0.0.1", 9999))

with open('client_udp.py', 'rb') as f:
    for i in f:
        client.send(i)
        msg = client.recv(1024)
        if msg != b'success':
            break
    pass
client.send('quit'.encode())
client.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
