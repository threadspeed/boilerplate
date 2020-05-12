---
title: python script test green cross thread lock (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test green cross thread lock'

Functions in program: 
* `def spawn_loop_lock(name):`
* `def loop_lock(name):`
* `def hold_lock():`

Modules used in program: 
* `import time`
* `import random`
* `import threading`

## python test green cross thread lock

Python mysql example: test green cross thread lock

```python
import threading
import random
import time
from contextlib import contextmanager
from eventlet import GreenPool

# from swift.common.utils import EventFdMutex as Lock
# from threading import RLock as Lock
from swift.common.utils import PipeMutex as Lock

running = True

has_lock = set()

lock = Lock()

random.seed(42)
count = 0


@contextmanager
def hold_lock():
    global count
    try:
        lock.acquire()
        count += 1
        yield
    finally:
        lock.release()


def loop_lock(name):
    global running
    while running:
        with hold_lock():
            has_lock.add(name)
            time.sleep(random.random() * 0.01)
            if len(has_lock) > 1:
                running = False
                raise Exception('%s found double locked %r' % (
                    name, has_lock))
            has_lock.remove(name)
        time.sleep(random.random() * 0.01)


def spawn_loop_lock(name):
    p = GreenPool()
    for i in range(100):
        p.spawn(loop_lock, name + '-gid-%d' % i)
    p.waitall()


threads = []
for i in range(30):
    t = threading.Thread(target=spawn_loop_lock, args=('thread-%d' % i,))
    t.start()
    threads.append(t)

start = time.time()
try:
    while running and time.time() - start < 30:
        print(has_lock)
        time.sleep(1)
except KeyboardInterrupt:
    print('shutting down...')
running = False
for t in threads:
    t.join()
print(count)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
