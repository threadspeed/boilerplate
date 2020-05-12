---
title: python script 01 run with block (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '01 run with block'

Functions in program: 
* `def worker(x,y):`

Modules used in program: 
* `import logging`
* `import threading`

## python 01 run with block

Python example: 01 run with block

```python
import threading
import logging
logger = logging.getLogger(__name__)
logging.basicConfig(level=logging.DEBUG, format="%(levelname)s %(threadName)-10s %(message)s")

def worker(x,y):
    logger.info("Worker: sum %s" % (x+y))

threads = []
for i in range(5):
    t = threading.Thread(target=worker, args=[1,2])
    threads.append(t)
    t.start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
