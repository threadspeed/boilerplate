---
title: python script 11 wait with condition (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '11 wait with condition'

Functions in program: 
* `def producer(cond):`
* `def consumer(cond):`

Modules used in program: 
* `import time`
* `import threading`
* `import logging`

## python 11 wait with condition

Python mysql example: 11 wait with condition

```python
import logging
import threading
import time

logging.basicConfig(level=logging.DEBUG,
                    format='%(asctime)s (%(threadName)-2s) %(message)s',
                    )

def consumer(cond):
    """wait for the condition and use the resource"""
    logging.debug('Starting consumer thread')
    t = threading.currentThread()
    with cond:
        cond.wait()
        logging.debug('Resource is available to consumer')

def producer(cond):
    """set up the resource to be used by the consumer"""
    logging.debug('Starting producer thread')
    with cond:
        logging.debug('Making resource available')
        cond.notifyAll() #hmm.

condition = threading.Condition()
c1 = threading.Thread(name='c1', target=consumer, args=(condition,))
c2 = threading.Thread(name='c2', target=consumer, args=(condition,))
p = threading.Thread(name='p', target=producer, args=(condition,))

c1.start()
c2.start()
time.sleep(0.1)
p.start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
