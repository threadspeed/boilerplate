---
title: python script 14 producer consumer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '14 producer consumer'


Modules used in program: 
* `import logging`
* `import threading`
* `import time`

## python 14 producer consumer

Python example: 14 producer consumer

```python
import time
import threading
import logging
logger = logging.getLogger("")
logging.basicConfig(level=logging.NOTSET, format="%(threadName)s -- %(message)s")

"""
inspired with
Understanding Threading in Python LG #107 http://linuxgazette.net/107/pai.html
"""

class itemQ(object):
    def __init__(self):
        self.count=0

    def display(self):
        logger.info("\t\t\t\t\tcount: %s" % self.count)

    def produce(self):
        self.count += 1
        self.display()

    def consume(self):
        self.count -= 1
        if self.count < 0:
            raise ValueError
        self.display()

    def isEmpty(self):
        return self.count <= 0

class Producer(threading.Thread):
    def __init__(self,condition, itemq, times=100, sleeptime=0.01):
        threading.Thread.__init__(self)
        self.cond=condition
        self.itemq=itemq
        self.sleeptime=sleeptime
        self.times = times

    def run(self):
        cond=self.cond
        itemq=self.itemq

        for i in xrange(self.times):
            with cond:
                logger.info("Produced One Item")
                itemq.produce()
                cond.notifyAll()
            time.sleep(self.sleeptime)


class Consumer(threading.Thread):
    def __init__(self,condition,itemq, times=100, sleeptime=0.015):
        threading.Thread.__init__(self)
        self.cond=condition
        self.itemq=itemq
        self.sleeptime=sleeptime
        self.times = times

    def run(self):
        cond=self.cond
        itemq=self.itemq
        for i in xrange(self.times):
            time.sleep(self.sleeptime)
            with cond:
                while itemq.isEmpty():
                    cond.wait()
                itemq.consume()
                logger.info("Consumed One Item")
        
if __name__=="__main__":

    q=itemQ()

    cond=threading.Condition()

    pro=Producer(cond,q)
    cons1=Consumer(cond,q)
    cons1.daemon = True
    cons2=Consumer(cond,q)
    cons2.daemon = True
    pro.daemon = True
    pro.start()
    cons1.start()
    cons2.start()
    ct = threading.current_thread()
    for t in threading.enumerate():
        if ct != t:
            t.join(5)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
