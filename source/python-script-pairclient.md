---
title: python script pairclient (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pairclient'


Modules used in program: 
* `import time`
* `import sys`
* `import random`
* `import zmq`

## python pairclient

Python mysql example: pairclient

```python
import zmq
import random
import sys
import time

port = "5556"

if len(sys.argv) > 1:
    port =  sys.argv[1]
    int(port)

context = zmq.Context()
socket = context.socket(zmq.REQ)
socket.connect("tcp://0.0.0.0:%s" % port)

messaggio='g.region -p'
socket.send_string(messaggio)
msg = socket.recv()
print(msg)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
