---
title: python script 08 unlock (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '08 unlock'

Functions in program: 
* `def worker(c):`

Modules used in program: 
* `import time`
* `import threading`
* `import random`
* `import logging`

## python 08 unlock

Python mysql example: 08 unlock

```python
import logging
import random
import threading
import time

logging.basicConfig(level=logging.DEBUG,
                    format='(%(threadName)-10s) %(message)s',
                    )
                    
class Counter(object):
    def __init__(self, start=0):
        self.value = start
    def increment(self):
        self.value = self.value + 1

def worker(c):
    for i in range(10000):
        time.sleep(random.random()*0.0001)
        c.increment()
    logging.debug('Done')

counter = Counter()
for i in range(3):
    t = threading.Thread(target=worker, args=(counter,))
    t.start()

logging.debug('Waiting for worker threads')
main_thread = threading.currentThread()
for t in threading.enumerate():
    if t is not main_thread:
        t.join()
logging.debug('Counter: %d', counter.value)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
