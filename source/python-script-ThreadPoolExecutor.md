---
title: python script ThreadPoolExecutor (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ThreadPoolExecutor'

Functions in program: 
* `def thread_function(name):`

Modules used in program: 
* `import concurrent.futures`
* `import time`
* `import threading`
* `import logging`

## python ThreadPoolExecutor

Python example: ThreadPoolExecutor

```python
import logging
import threading
import time
import concurrent.futures


def thread_function(name):
    logging.info("Thread %s: starting", name)
    time.sleep(2)
    logging.info("Thread %s: finishing", name)

if __name__ == "__main__":
    format = "%(asctime)s: %(message)s"
    logging.basicConfig(format=format, level=logging.INFO,
                        datefmt="%H:%M:%S")
    #ThreadPoolExecutor
    #会自动调用.join()方法
    with concurrent.futures.ThreadPoolExecutor(max_workers=3) as executor:
        executor.map(thread_function, range(3))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
