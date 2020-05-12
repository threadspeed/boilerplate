---
title: python script test threads (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test threads'

Functions in program: 
* `def main():`
* `def test_thread():`
* `def thread_code():`
* `def test_basic():`
* `def allocate_pointer():`
* `def store_pointer(obj, ptr):`

Modules used in program: 
* `import random`
* `import threading`
* `import boehmgc as gc`

## python test threads

Python mysql example: test threads

```python
from __future__ import print_function, division
import boehmgc as gc
from ctypes import c_void_p, POINTER, cast, memmove, addressof, sizeof, c_size_t
import threading
import random

def store_pointer(obj, ptr):
    memmove(c_void_p(obj), addressof(c_void_p(ptr)), sizeof(c_void_p))

def allocate_pointer():
    ptrsize = sizeof(c_void_p)
    sz = ptrsize * max(1, int(random.random()*1024*2))
    gcptr = gc.malloc(sz)
    box = gc.malloc_uncollectable(ptrsize)
    store_pointer(box, gcptr)
    return box


def test_basic():
    for i in range(100):
        ptrs = [allocate_pointer() for x in range(1024)]
        for p in ptrs:
            gc.free(p)

def thread_code():
    gc.register_thread()
    try:
        ptrs = [allocate_pointer() for x in range(100)]
        for p in ptrs:
            gc.free(p)
    finally:
        gc.unregister_thread()


def test_thread():
    numthreads = 100
    threads = []
    usage = gc.usage()

    for _ in range(numthreads):
        th = threading.Thread(target=thread_code)
        threads.append(th)

    for th in threads:
        th.start()

    for th in threads:
        th.join()


def main():
    gc.init()
    gc.enable_threads()

    # Repeat our test several times, the % free should be close to 100%.
    # Since Boehm is not precise, we may never get 100% collection.
    # Another metric is the heapsize, the heapsize shall not increase as we
    # repeat the test.  The first iteration should have
    for i in range(20):
        print('round', i)
        test_basic()
        test_thread()

        gc.collect()
        usage = gc.usage()
        print(usage)
        print("% free", 100*usage.freesize/usage.heapsize)

if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
