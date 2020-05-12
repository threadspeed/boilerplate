---
title: python script ProducerAndConsumer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ProducerAndConsumer'

Functions in program: 
* `def main():`

Modules used in program: 
* `import time`
* `import threading`
* `import random`

## python ProducerAndConsumer

Python example: ProducerAndConsumer

```python
from queue import Queue
import random
import threading
import time

#Producer thread
class Producer(threading.Thread):
    def __init__(self, t_name, queue):
        threading.Thread.__init__(self, name=t_name)
        self.data=queue
    def run(self):
        i = 0
        while True:
            i = i+1
            print("%s: %s is producing %d to the queue!" % (time.ctime(), self.getName(), i))
            self.data.put(i)
            time.sleep(random.randrange(10)/5)
        print( "%s: %s finished!" % (time.ctime(), self.getName()))

#Consumer thread
class Consumer(threading.Thread):
    def __init__(self, t_name, queue):
        threading.Thread.__init__(self, name=t_name)
        self.data=queue
    def run(self):
        while True:
            val = self.data.get()
            print("%s: %s is consuming. %d in the queue is consumed!" % (time.ctime(), self.getName(), val))
            time.sleep(random.randrange(10)/5)
        print( "%s: %s finished!" % (time.ctime(), self.getName()))

#Main thread
def main():
    queue = Queue()
    producer = Producer('Pro.', queue)
    consumer = Consumer('Con.', queue)
    producer.start()
    consumer.start()
    producer.join()
    consumer.join()
    print( 'All threads terminate!')
 
if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
