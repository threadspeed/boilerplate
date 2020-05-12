---
title: python script Sserver (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Sserver'

Functions in program: 
* `def clientthread(conn):`

Modules used in program: 
* `import random`
* `import string`
* `import socket`

## python Sserver

Python mysql example: Sserver

```python
import socket
from thread import *
import string
import random

try:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(('127.0.0.1', 9900))
    s.listen(10)
    c = {}
except KeyboardInterrupt:
    exit(0)
# def generation(conn):
#     sesion = str(random.randint(1, 1024))
#     data = conn.recv(1024)
#     e = data.split('>')
#     if len(e) > 1:
#         try:
#             c[e[1]]
#         except:
#             c[e[1]] = []
#         sesion = e[0]
#         c[e[1]].append(e[0] +   '>' +e[2])
#         data = 'Session created'
#     else:
#         data = 'Error'
            

def clientthread(conn):
    while 1:
        data = conn.recv(1024)
        e = data.split('>')
        if len(e) == 3:
            if e[1] == 'show':
                try:
                    m = ''
                    for i in range(0, len(c[e[0]])):
                        m = m + c[e[0]][i]
                        if i != (len(c[e[0]])-1):
                            m = m + '\n'
                        if m == '':
                            data = 'No messages'
                        else:
                            data = m
                    del c[e[0]]
                except:
                    data = 'No messages'
            else:
                try:
                    c[e[1]]
                except:
                    c[e[1]] = []
                c[e[1]].append(e[0] + '>' +e[2])
                data = 'Ok'
        else:
            data = 'Error'
        conn.send(data)
    conn.close()
while 1:
    conn, addr = s.accept()
    start_new_thread(clientthread , (conn,))
    start_new_thread(generation , (conn,))
s.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
