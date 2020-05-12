---
title: python script with-lock (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'with-lock'


Modules used in program: 
* `import concurrent.futures`
* `import time`
* `import threading`
* `import logging`

## python with-lock

Python example: with-lock

```python
import logging
import threading
import time
import concurrent.futures

class FakeDatabase:
    def __init__(self):
        self.value = 0
        self._lock = threading.Lock()
    
    #自行管理所的acquire和release
    def locked_update2(self,name):
        self._lock.acquire()
        local_copy = self.value
        local_copy += 1
        time.sleep(0.1)
        self.value = local_copy
        self._lock.release()

    def locked_update(self, name):
        logging.info("Thread %s: starting update", name)
        logging.debug("Thread %s about to lock", name)
        #with自行管理锁获取和释放
        with self._lock:
            logging.debug("Thread %s has lock", name)
            local_copy = self.value
            local_copy += 1
            time.sleep(0.1)
            self.value = local_copy
            logging.debug("Thread %s about to release lock", name)
        logging.debug("Thread %s after release", name)
        logging.info("Thread %s: finishing update", name)

if __name__ == "__main__":
    format = "%(asctime)s: %(message)s"
    logging.basicConfig(format=format, level=logging.INFO,
                        datefmt="%H:%M:%S")

    database = FakeDatabase()
    logging.info("Testing update. Starting value is %d.", database.value)
    with concurrent.futures.ThreadPoolExecutor(max_workers=2) as executor:
        for index in range(2):
            executor.submit(database.locked_update2, index) #submit()告诉线程去运行函数
    logging.info("Testing update. Ending value is %d.", database.value)




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
