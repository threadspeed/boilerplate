---
title: python script server (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'server'

Functions in program: 
* `def serve():`
* `def handle_sigint(signal, frame):`
* `def cleanup():`

Modules used in program: 
* `import time`
* `import sys`
* `import socket`
* `import signal`
* `import random`
* `import os`

## python server

Python mysql example: server

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import os
import random
import signal
import socket
import sys
import time

BUFFER_SIZE = 128
SOCKET_PATH = '/tmp/echo.sock'

def cleanup():
  try:
    os.unlink(SOCKET_PATH)
  except OSError:
    return


def handle_sigint(signal, frame):
  cleanup()
  quit()

def serve():
  cleanup()

  sock = socket.socket(socket.AF_UNIX)
  sock.bind(SOCKET_PATH)
  sock.listen(1)
  print("Waiting for new connection.")

  conn, addr = sock.accept()
  print("Connected: %s" % addr)

  while True:
    try:
      conn.sendall(str(random.random()))
      res = conn.recv(BUFFER_SIZE)
      print("Sent: %s %s" % (data, res))
      time.sleep(0.1)
    except IOError:
      conn.close()
      print("Disconnected")
      serve()
      break

if __name__ == '__main__':
  signal.signal(signal.SIGPIPE, signal.SIG_IGN)
  sys.stdout = os.fdopen(sys.stdout.fileno(), 'w', 0)
  signal.signal(signal.SIGINT, handle_sigint)

  serve()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
