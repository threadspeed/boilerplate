---
title: python script mongodb perf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mongodb perf'


Modules used in program: 
* `import random`
* `import time`
* `import md5`
* `import pymongo`
* `import sys`

## python mongodb perf

Python example: mongodb perf

```python
import sys
import pymongo
import md5
import time
import random

host = 'host:port'
conn = pymongo.Connection([host])
db = conn.test

ITEM_COUNT = 1000000

SET_TIMES = []
for c in range(0, 10):
    t1 = time.time() * 1000
    for i in range(0, 1000):
        key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
        val = key * 4
        db.mycoll.save({'_id': key, 'val': val}, safe=True)
    t2 = time.time() * 1000
    SET_TIMES.append(t2 - t1)
print(str(SET_TIMES))
avg = sum(SET_TIMES) / 10
print('SET TIME(1000 items): %f ms' % (avg))

GET_TIMES = []
for c in range(0, 10):
    t1 = time.time() * 1000
    for i in range(0, 1000):
        key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
        db.mycoll.find_one(key)
    t2 = time.time() * 1000
    GET_TIMES.append(t2 - t1)
avg = sum(GET_TIMES) / 10
print('GET TIME(1000 items): %f ms' % (avg))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
