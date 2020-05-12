---
title: python script prodcom queue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'prodcom queue'

Functions in program: 
* `def consumer(pipeline, event):`
* `def producer(pipeline, event):`

Modules used in program: 
* `import random`
* `import concurrent.futures`
* `import time`
* `import queue`
* `import threading`
* `import logging`

## python prodcom queue

Python mysql example: prodcom queue

```python
import logging
import threading
import queue
import time
import concurrent.futures
import random

#使用Queue是解决生产者/消费者最好的解决方案，封装了lock操作
#多线程编程调试很困难，比如 import random 如果不写，代码不会报错
class Pipeline(queue.Queue):
    def __init__(self):
        super().__init__(maxsize=10)

    def get_message(self, name):
        logging.debug("%s:about to get from queue", name)
        value = self.get()
        logging.debug("%s:got %d from queue", name, value)
        return value

    def set_message(self, value, name):
        logging.debug("%s:about to add %d to queue", name, value)
        self.put(value)
        logging.debug("%s:added %d to queue", name, value)

def producer(pipeline, event):
    """Pretend we're getting a number from the network."""
    while not event.is_set():
        message = random.randint(1, 101)
        logging.info("Producer got message: %s", message)
        pipeline.set_message(message, "Producer")

    logging.info("Producer received EXIT event. Exiting")

def consumer(pipeline, event):
    """Pretend we're saving a number in the database."""
    while not event.is_set() or not pipeline.empty():
        message = pipeline.get_message("Consumer")
        logging.info(
            "Consumer storing message: %s  (queue size=%s)",
            message,
            pipeline.qsize(),
        )

    logging.info("Consumer received EXIT event. Exiting")

if __name__ == "__main__":
    format = "%(asctime)s: %(message)s"
    logging.basicConfig(format=format, level=logging.INFO,
                        datefmt="%H:%M:%S")
    # logging.getLogger().setLevel(logging.DEBUG)

    pipeline = Pipeline()
    event = threading.Event()
    with concurrent.futures.ThreadPoolExecutor(max_workers=2) as executor:
        executor.submit(producer, pipeline, event)
        executor.submit(consumer, pipeline, event)

        #threading.Event对象允许一个线程发出事件信号，而许多其他线程可以等待该事件发生。
        #可以用来暂停线程的运行
        time.sleep(0.1)
        logging.info("Main: about to set event")
        event.set()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
