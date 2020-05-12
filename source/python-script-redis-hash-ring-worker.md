---
title: python script redis-hash-ring-worker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'redis-hash-ring-worker'


Modules used in program: 
* `import signal`
* `import random`
* `import threading`
* `import gevent`

## python redis-hash-ring-worker

Python example: redis-hash-ring-worker

```python
from redis import Redis
from redis_hashring import RingNode
import gevent
import threading
import random
import signal
N_KEYS = 10

# we cannot use thread object
class Listener():#threading.Thread):
    def __init__(self, redis, ring_node):
        #threading.Thread.__init__(self)
        self.redis = redis
        self.ring_node  = ring_node
        self.pubsub = self.redis.pubsub()

        self.kill_now = False
        signal.signal(signal.SIGINT, self.exit_gracefully)
        signal.signal(signal.SIGTERM, self.exit_gracefully)

    def exit_gracefully(self,signum, frame):
        ring_node.gevent_stop()
        print('Stopping worker...')
        self.kill_now = True

    def work(self, item):
        print('Working on item:', item)

    def run(self):
        while True:
            keys = [str(key) for key in range(N_KEYS) if self.ring_node.contains(str(key))]
            print(keys)
            random.shuffle(keys)

            for key in keys:
                item = self.redis.lpop(key)

                if item is not None:
                    self.work(item)

            gevent.sleep(2)

            if self.kill_now:
                return

if __name__ == "__main__":
    redis = Redis()
    ring_node = RingNode(redis, 'ring')
    ring_node.gevent_start()

    client = Listener(redis, ring_node)
    client.run()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
