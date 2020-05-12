---
title: python script boehmgc (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'boehmgc'

Functions in program: 
* `def usage():`
* `def unregister_thread():`
* `def register_thread():`
* `def enable_threads():`
* `def collect_little():`
* `def collect():`
* `def free(ptr):`
* `def malloc_uncollectable(sz):`
* `def malloc_atomic(sz):`
* `def malloc(sz):`
* `def dump():`
* `def init():`

## python boehmgc

Python mysql example: boehmgc

```python
from ctypes import c_size_t, c_void_p, c_int, CDLL, byref
from collections import namedtuple

libboehm = CDLL('./libboehm.so')

libboehm.boehm_free.argtypes = [c_void_p]

# Set allocator
for fn in [libboehm.boehm_malloc,
           libboehm.boehm_malloc_uncollectable]:
    fn.argtypes = [c_size_t]
    fn.restype = c_void_p

libboehm.boehm_register_finalizer.argtypes = [c_void_p, c_void_p, c_void_p]

libboehm.boehm_register_thread.restype = c_int

def init():
    libboehm.boehm_init()

def dump():
    libboehm.boehm_dump()

def malloc(sz):
    return libboehm.boehm_malloc(sz)

def malloc_atomic(sz):
    return libboehm.boehm_malloc_atomic(sz)

def malloc_uncollectable(sz):
    return libboehm.boehm_malloc_uncollectable(sz)

def free(ptr):
    libboehm.boehm_free(ptr)

def collect():
    libboehm.boehm_collect()

def collect_little():
    libboehm.boehm_collect_little()

# def register_finalizer(obj, dtor, data):
#     pass

def enable_threads():
    libboehm.boehm_allow_threads()

def register_thread():
    if libboehm.boehm_register_thread():
        raise RuntimeError("GC failed to register thread")

def unregister_thread():
    if libboehm.boehm_unregister_thread():
        raise RuntimeError("GC failed to unregister thread")

def usage():
    heapsize = c_size_t()
    freesize = c_size_t()
    libboehm.boehm_get_usage(byref(heapsize), byref(freesize))
    return namedtuple("gc_usage", ["heapsize", "freesize"])(
        heapsize=heapsize.value, freesize=freesize.value)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
