---
title: python script memcached perf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'memcached perf'


Modules used in program: 
* `import random`
* `import time`
* `import md5`
* `import pylibmc`
* `import sys`

## python memcached perf

Python mysql example: memcached perf

```python
## memcached, Couchbaseで使用

import sys
import pylibmc
import md5
import time
import random

host = 'host:port'
mc = pylibmc.Client([host])

ITEM_COUNT = 1000000

SET_TIMES = []
for c in range(0, 10):
    t1 = time.time() * 1000
    for i in range(0, 1000):
        key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
        val = key * 4
        mc.set(key, val)
    t2 = time.time() * 1000
    SET_TIMES.append(t2 - t1)
avg = sum(SET_TIMES) / 10
print('SET TIME(1000 items): %f ms' % (avg))

GET_TIMES = []
for c in range(0, 10):
    t1 = time.time() * 1000
    for i in range(0, 1000):
        key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
        mc.get(key)
    t2 = time.time() * 1000
    GET_TIMES.append(t2 - t1)
avg = sum(GET_TIMES) / 10
print('GET TIME(1000 items): %f ms' % (avg))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
