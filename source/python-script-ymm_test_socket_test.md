---
title: python script ymm test socket test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ymm test socket test'

Functions in program: 
* `def main():`

Modules used in program: 
* `import socket`

## python ymm test socket test

Python mysql example: ymm test socket test

```python
#-*- coding:UTF-8 -*-
import socket
"""tcp socket 套接字
s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)

#udp socket套接字
udps = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
s.close()
"""
def main():
    udp_socket = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
    udp_socket.sendto(b'haha',('127.0.0.1',8080))
    udp_socket.close()

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
