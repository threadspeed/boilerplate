---
title: python script communication (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'communication'


Modules used in program: 
* `import zmq`

## python communication

Python mysql example: communication

```python
import zmq
 
class Communication:
    def __init__(self, port):
        context = zmq.Context()
        self.port = port
        self.socket = context.socket(zmq.PAIR)
 
    def connect(self):
        self.socket.connect("tcp://localhost:%s" % self.port)
 
    def bind(self):
        self.socket.bind("tcp://*:%s" % self.port)
    
    def sender(self):
        while True:
            msg = raw_input("> ")
            self.socket.send(msg)
            
    def reciever(self):
        while True:
            msg = self.socket.recv()
            print("> " + msg)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
