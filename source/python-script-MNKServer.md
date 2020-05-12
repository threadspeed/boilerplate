---
title: python script MNKServer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MNKServer'

Functions in program: 
* `def takeSnapshot(device):`
* `def randomMove(device, c):`
* `def doMove(device, c, move):`

Modules used in program: 
* `import socket`
* `import time`
* `import random`

## python MNKServer

Python example: MNKServer

```python
#!/usr/bin/env monkeyrunner

from com.android.monkeyrunner import MonkeyRunner
import random
import time
import socket

MOVES = ("LEFT", "RIGHT", "DOWN", "UP")


def doMove(device, c, move):
    if move in "LEFT":
        device.drag(c, (c[0] - 100, c[1]), 0.3, 15)
    elif move in "RIGHT":
        device.drag(c, (c[0] + 100, c[1]), 0.3, 15)
    elif move in "DOWN":
        device.drag(c, (c[0], c[1] + 100), 0.3, 15)
    elif move in "UP":
        device.drag(c, (c[0], c[1] - 100), 0.3, 15)
    time.sleep(0.3)


def randomMove(device, c):
    i = random.randint(0,3)
    doMove(device, c, MOVES[i])

def takeSnapshot(device):
    result = device.takeSnapshot()
    ## Writes the screenshot to a file
    result.writeToFile('shot1.png', 'png')


if __name__ == "__main__":
    device = MonkeyRunner.waitForConnection()

    W = device.getProperty('display.width')
    H = device.getProperty('display.height')

    c = (int(W) / 2, int(H) / 2)

    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind(('localhost', 4456))
    server.listen(5)
    while True:
        cn, addr = server.accept()
        while True:
            buf = cn.recv(64)
            if not buf:
                break
            if len(buf) > 0:
                print(buf)
                if "MOVE" in buf:
                    randomMove(device, c)
                elif "SCREEN" in buf:
                    takeSnapshot(device)
                elif buf in MOVES:
                    doMove(device, c, buf)
                cn.send("OK")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
