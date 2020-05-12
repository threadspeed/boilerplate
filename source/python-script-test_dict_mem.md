---
title: python script test dict mem (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test dict mem'

Functions in program: 
* `def f7():`
* `def f6():`
* `def f5():`
* `def f4():`
* `def f3():`
* `def f2_3():`
* `def f2_2():`
* `def f2():`
* `def f2():`
* `def f1():`
* `def max_rss():`
* `def length():`
* `def statm():`
* `def pmem():`
* `def dmem():`
* `def timing(f):`

Modules used in program: 
* `import random`
* `import resource`
* `import psutil`
* `import time`
* `import sys`

## python test dict mem

Python mysql example: test dict mem

```python
import sys
from six.moves import range
import time
import psutil
import resource
import random

M = 1024*1024
p = psutil.Process()
d = {}

def timing(f):
    return f
    def _():
        t1 = time.time()

        for i in range(1000):
            r = f()
        t2 = time.time()
        return r, (t2-t1)
    return _


@timing
def dmem():
    return sys.getsizeof(d)/M


@timing
def pmem():
    return p.memory_info().rss/M


@timing
def statm():
    with open('/proc/self/statm','r') as f:
        v = f.readline()
        return int(v.split()[1])*4096/M

@timing
def length():
    return len(d)


def max_rss():
    return resource.getrusage(resource.RUSAGE_SELF).ru_maxrss * 1024


def f1():
    for i in range(M * 1000):
        #d[i] = i
        d[i] = str(i) * 10
        if i % M == 0:
            print(i>>20,  statm(), pmem(), dmem(), length())


def f2():
    last_rss = 0
    last_dsize = 0
    for i in range(M * 1000):
        d[i] = i
        # d[int(i/2)] = i
        d[i] = str(i) * 10
        rss = statm()
        dsize = sys.getsizeof(d)
        if dsize != last_dsize:
            print("%d %s:  mem %d + %d -> %d, max %d; size %d + %d -> %d" % (i, hex(i), last_rss, rss-last_rss, rss, max_rss() /M, last_dsize/M, (dsize - last_dsize)/M, dsize/M))

        last_dsize = dsize
        last_rss = rss

def f2():
    last_rss = 0
    last_dsize = 0
    for i in range(M * 1000):
        d[i] = i
        # d[int(i/2)] = i
        d[i] = str(i) * 10
        rss = statm()
        dsize = sys.getsizeof(d)
        if dsize != last_dsize:
            print("%d %s:  mem %d + %d -> %d, max %d; size %d + %d -> %d" % (i, hex(i), last_rss, rss-last_rss, rss, max_rss() /M, last_dsize/M, (dsize - last_dsize)/M, dsize/M))

        last_dsize = dsize
        last_rss = rss


def f2_2():
    last_rss = 0
    last_dsize = 0

    S = 0x1aaaaaa + 1
    vs = list(range(S))
    random.shuffle(vs)

    for i in vs:
        d[i] = i
        rss = statm()
        dsize = sys.getsizeof(d)
        if dsize != last_dsize:
            print("%d %s:  mem %d + %d -> %d, max %d; size %d + %d -> %d" % (i, hex(i), last_rss, rss-last_rss, rss, max_rss() /M, last_dsize/M, (dsize - last_dsize)/M, dsize/M))

        last_dsize = dsize
        last_rss = rss


def f2_3():
    last_rss = 0
    last_dsize = 0
    for i in range(M * 1000):
        k = random.randint(0, 1<<30)
        d[k] = i
        rss = statm()
        dsize = sys.getsizeof(d)
        if dsize != last_dsize:
            print("%d %s:  mem %d + %d -> %d, max %d; size %d + %d -> %d" % (i, hex(i), last_rss, rss-last_rss, rss, max_rss() /M, last_dsize/M, (dsize - last_dsize)/M, dsize/M))

        last_dsize = dsize
        last_rss = rss


def f3():
    import random
    d = dict()
    t = time.time()
    for i in range(S):
        #k = (i, i, i, i)
        k = i
        d[k] = i
    t = time.time() - t
    print("dict ", t, statm())
    del d


def f4():
    S = 0xaaaaaa-1
    N = 100
    dd = [dict() for i in range(N)]
    t = time.time()
    for i in range(S):
        #k = (i, i, i, i)
        k = i
        h = hash(k) % N
        dd[h][k] = i
    t = time.time() - t
    print("%d dicts " % N, t, statm())


def f5():
    import random

    S = 0xaaaaaa-1 + 100
    vs = list(range(S))
    random.shuffle(vs)

    d = dict()
    t = time.time()
    for i in vs:
        #k = i
        #k = str(i)
        k = (i, i, i, i)
        d[k] = i
    t = time.time() - t
    print("dict ", t, statm())
    del d



def f6():
    import random

    S = 0xaaaaaa-1+100
    vs = list(range(S))
    random.shuffle(vs)

    N = 100
    dd = [dict() for i in range(N)]
    t = time.time()
    for i in vs:
        #k = i
        #k = str(i)
        k = (i, i, i, i)
        h = hash(k) % N
        dd[h][k] = i
    t = time.time() - t
    print("dict ", t, statm())


def f7():
    import random
    sizes0 = [0xaaaaaa, 0x1555555, 0x2aaaaaa]
    sizes = []
    for s in sizes0:
        sizes.append(s-1)
        sizes.append(s)
    print(sizes)

    def _(n):
        random.seed(1)
        d = {}
        dd = [dict() for i in range(n)]
        target_idx = 0
        target_count = sizes[target_idx]
        time_mems = []
        t0 = time.time()
        msg = "%3d" % n
        for i in range(sizes[-1] + 1):
            k = "%07x" % (i, )
            if n == 1:
                d[k] = i
            else:
                h = hash(k) % n
                dd[h][k] = i
            if i == target_count:
                m = statm()
                #print(hex(i), m)
                t = time.time() - t0
                time_mems.append((i, t, m))
                msg += " (0x%07x %.2fs %5dM)" % (i,t,m)
                target_idx += 1
                if target_idx < len(sizes):
                    target_count = sizes[target_idx]
        del d
        del dd
        print(msg)
        return time_mems

    _(1)
    _(139)


f7()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
