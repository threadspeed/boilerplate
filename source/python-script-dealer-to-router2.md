---
title: python script dealer-to-router2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dealer-to-router2'

Functions in program: 
* `def main():`
* `def receiver():`
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

## python dealer-to-router2

Python example: dealer-to-router2

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
    worker.bind("ipc://routing.ipc")

    total = 0
    while True:
        request = worker.recv_multipart()
        print("Worker - request: ", request)
        client_id, msg_id, msg = request
        if random.choice([True, True, False]):  # should I respond?
            response = process_request(msg)
            # worker.send_multipart([client_id, msg_id, response])
            worker.send_multipart([b'B', msg_id, response])
        finished = msg == b"END"
        if finished:
            break

        if msg == b'STATUS':
            response = "Worker received: %s" % total
            worker.send_multipart([b'B', msg_id, response])
        total += 1


context = zmq.Context.instance()
client = context.socket(zmq.DEALER)
client.setsockopt(zmq.IDENTITY, b'A')
client.connect("ipc://routing.ipc")

Thread(target=worker).start()


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


def receiver():
    context = zmq.Context.instance()
    client = context.socket(zmq.DEALER)
    client.setsockopt(zmq.IDENTITY, b'B')
    client.connect("ipc://routing.ipc")
    client.send_multipart([b'no-uid', b'hello'])

    poll = zmq.Poller()
    poll.register(client, zmq.POLLIN)

    POLL_TIMEOUT = 2000

    while True:
        socks = dict(poll.poll(POLL_TIMEOUT))
        if socks.get(client) == zmq.POLLIN:
            reply = client.recv_multipart(zmq.NOBLOCK)
            print("Received:", reply)


Thread(target=receiver).start()

time.sleep(1)


def main():
    requests = {}

    for i in range(10):
        work = b"This is the workload {0}".format(i)
        uid = dispatch(work)
        requests[uid] = {'work': work}

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
