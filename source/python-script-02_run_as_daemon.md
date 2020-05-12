---
title: python script 02 run as daemon (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '02 run as daemon'

Functions in program: 
* `def worker(x,y):`

Modules used in program: 
* `import random`
* `import time`
* `import logging`
* `import threading`

## python 02 run as daemon

Python example: 02 run as daemon

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


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
