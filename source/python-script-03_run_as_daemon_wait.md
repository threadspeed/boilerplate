---
title: python script 03 run as daemon wait (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '03 run as daemon wait'

Functions in program: 
* `def worker(x,y):`

Modules used in program: 
* `import random`
* `import time`
* `import logging`
* `import threading`

## python 03 run as daemon wait

Python example: 03 run as daemon wait

```python
import threading
import logging
import time
import random

logger = logging.getLogger(__name__)
logging.basicConfig(level=logging.DEBUG, format="%(levelname)s %(threadName)-10s %(message)s")

def worker(x,y):
    n = random.random()
    logger.info("Worker: start wait --%s" % n)
    time.sleep(n)
    logger.info("Worker: sum %s" % (x+y))

threads = []
for i in range(5):
    t = threading.Thread(target=worker, args=[1,2])
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
