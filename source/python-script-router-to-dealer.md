---
title: python script router-to-dealer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'router-to-dealer'

Functions in program: 
* `def main():`
* `def receive():`
* `def dispatch(r):`
* `def worker():`
* `def process_request(request):`

Modules used in program: 
* `import zmq`
* `import uuid`
* `import random`
* `import time`
* `import pprint`

## python router-to-dealer

Python example: router-to-dealer

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# ROUTER to DEALER (1->N)
# this can be used for a client with many workers

import pprint
import time
import random
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
    worker = context.socket(zmq.DEALER)
    worker.setsockopt(zmq.IDENTITY, b'A')
    worker.connect("ipc://routing.ipc")

    total = 0
    while True:
        # We receive one part, with the workload
        request = worker.recv_multipart()
        print("Worker - request: ", request)
        msg_id, msg = request
        if random.choice([True, True, False]):  # should I respond?
            response = process_request(msg)
            worker.send_multipart([msg_id, response])

        finished = msg == b"END"
        if finished:
            break

        if msg == b'STATUS':
            # print("A received: %s" % total)
            worker.send("A received: %s" % total)
        total += 1


context = zmq.Context.instance()
client = context.socket(zmq.ROUTER)
client.bind("ipc://routing.ipc")

Thread(target=worker).start()

# Wait for threads to stabilize
time.sleep(1)


def dispatch(r):
    to = b'A'
    uid = bytes(uuid.uuid4())
    r = client.send_multipart([to, uid, bytes(r)])
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
            ruid = r[1]
            requests[ruid]['response'] = r[2]

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
