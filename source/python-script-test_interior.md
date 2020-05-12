---
title: python script test interior (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test interior'

Functions in program: 
* `def main():`
* `def allocate_pointer():`
* `def store_pointer(obj, ptr):`

Modules used in program: 
* `import random`
* `import threading`
* `import boehmgc as gc`

## python test interior

Python example: test interior

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

    sz = ptrsize * 1024 #max(1, int(1024 * random.random()))
    gcptr = gc.malloc(sz)
    box = gc.malloc_uncollectable(ptrsize)
    # Point to the middle
    offset = int((sz-1)*random.random())
    assert gcptr + offset < gcptr + sz
    store_pointer(box, gcptr+offset)
    return box

def main():
    """
    Test interior pointer support.
    We are storing some offset to the pointer instead of the base
    """
    gc.init()

    ptrs = [allocate_pointer() for i in range(10000)]

    before = gc.usage()

    gc.collect()

    after = gc.usage()


    assert before == after, (before, after)

    for p in ptrs:
        gc.free(p)

    gc.collect()
    usage = gc.usage()
    assert usage.freesize == usage.heapsize


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
