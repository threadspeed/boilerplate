---
title: python script dealer-to-router (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dealer-to-router'

Functions in program: 
* `def main():`
* `def receive():`
* `def dispatch(r):`
* `def worker():`
* `def process_request(request):`

Modules used in program: 
* `import zmq`
* `import uuid`
* `import time`
* `import random`
* `import pprint`

## python dealer-to-router

Python mysql example: dealer-to-router

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# DEALER to ROUTER (N->1)
# this can be used for many client to use a central worker

import pprint
import random
import time
import uuid

from threading import Thread

import zmq


def process_request(request):
    n = 0
    try:
        n = int(request[-1])
    except:
        pass

    return bytes(n)


def worker():
    context = zmq.Context.instance()
    worker = context.socket(zmq.ROUTER)
    worker.connect("ipc://routing.ipc")

    total = 0
    while True:
        request = worker.recv_multipart()
        print("Worker - request: ", request)
        client_id, msg_id, msg = request
        if random.choice([True, True, False]):  # should I respond?
            response = process_request(msg)
            worker.send_multipart([client_id, msg_id, response])
        finished = msg == b"END"
        if finished:
            break

        if msg == b'STATUS':
            worker.send_multipart("A received: %s" % total)
        total += 1


context = zmq.Context.instance()
client = context.socket(zmq.DEALER)
client.setsockopt(zmq.IDENTITY, b'A')
client.bind("ipc://routing.ipc")

Thread(target=worker).start()

# Wait for threads to stabilize
time.sleep(1)


def dispatch(r):
    uid = bytes(uuid.uuid4())
    r = client.send_multipart([uid, bytes(r)])
    return uid


def receive():
    """
    Receive from client, DO NOT BLOCK, if there's nothing to receive just
    return None.
    """
    response = None
    try:
        response = client.recv_multipart(zmq.NOBLOCK)
    except:
        pass

    return response


def main():
    requests = {}

    for i in range(10):
        work = b"This is the workload {0}".format(i)
        uid = dispatch(work)
        requests[uid] = {'work': work}
        r = receive()
        if r is not None:
            print("Received: ", r)
            ruid = r[0]
            requests[ruid]['response'] = r[1]

    dispatch(b'END')

    time.sleep(1)
    print
    print("Report:")
    print('-'*20)
    pprint.pprint(requests)


if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
