---
title: python script 04 get current thread (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '04 get current thread'

Functions in program: 
* `def worker(x, y):`
* `def set_n(v):`
* `def get_n():`

Modules used in program: 
* `import operator as op`
* `import random`
* `import time`
* `import logging`
* `import threading`

## python 04 get current thread

Python mysql example: 04 get current thread

```python
import threading
import logging
import time
import random
import operator as op

logger = logging.getLogger(__name__)
logging.basicConfig(level=logging.DEBUG, format="%(levelname)s %(threadName)-10s %(message)s")

_local = threading.local()
def get_n():
    return getattr(_local, "n", None)

def set_n(v):
    _local.n = v

def worker(x, y):
    logger.info(threading.currentThread())
    logger.info(get_n())

    set_n(random.random())
    logger.info("Worker: start wait --%s" % get_n())
    time.sleep(get_n())
    logger.info("Worker: sum %s" % (x+y))

threads = []
for i in range(5):
    t = threading.Thread(target=worker, args=[100, 20])
    threads.append(t)
    t.daemon = True
    t.start()

for t in threads:
    # if set a timeout
    # t.join(0.001)
    t.join()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
