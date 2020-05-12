---
title: python script messages (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'messages'

Functions in program: 
* `def versionMessage():`
* `def makeMessage(cmd, payload):`

Modules used in program: 
* `import hashlib`
* `import random`
* `import struct`
* `import socket`
* `import time`

## python messages

Python example: messages

```python
import time
import socket
import struct
import random
import hashlib

def makeMessage(cmd, payload):
    magic = b'\xfb\xc0\xb6\xdb' # litecoin mainnet magic number
    command = str.encode(cmd + (12 - len(cmd)) * "\00")
    length = struct.pack("I", len(payload))
    check = hashlib.sha256(hashlib.sha256(payload).digest()).digest()[:4]
    return magic + command + length + check + payload

def versionMessage():
    version = struct.pack("i", 70015)
    services = struct.pack("Q", 0)
    timestamp = struct.pack("q", int(time.time()))

    addr_recv = struct.pack("Q", 0)
    addr_recv += struct.pack(">16s", b"127.0.0.1")
    addr_recv += struct.pack(">H", 9333)

    addr_from = struct.pack("Q", 0)
    addr_from += struct.pack(">16s", b"127.0.0.1")
    addr_from += struct.pack(">H", 9333)

    nonce = struct.pack("Q", random.getrandbits(64))
    user_agent = struct.pack("B", 0) # Anything
    height = struct.pack("i", 0) # Block number, doesn't matter

    payload = version + services + timestamp + addr_recv + addr_from + nonce + user_agent + height

    return payload


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
