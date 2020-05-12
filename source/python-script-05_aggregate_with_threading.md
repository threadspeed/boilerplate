---
title: python script 05 aggregate with threading (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '05 aggregate with threading'

Functions in program: 
* `def worker(x,y):`

Modules used in program: 
* `import time`
* `import random`
* `import logging`
* `import threading`

## python 05 aggregate with threading

Python mysql example: 05 aggregate with threading

```python
import threading
import logging
import random
import time

logger = logging.getLogger(__name__)
logging.basicConfig(level=logging.NOTSET, format="%(threadName)s -- %(message)s")

def worker(x,y):
    n = random.random()
    logger.info("start (wait %s)" % n)
    time.sleep(n)
    logger.info("%s+%s = %s" % (x,y, x+y))
    
for _ in xrange(10):
    t = threading.Thread(target=worker, args=[1,2])
    t.daemon = True
    t.start()

ct = threading.currentThread()

for t in threading.enumerate():
    if t != ct:
        t.join()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
