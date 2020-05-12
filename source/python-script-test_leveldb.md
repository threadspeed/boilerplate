---
title: python script test leveldb (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test leveldb'

Functions in program: 
* `def test(data, count):`
* `def timed_call(func, args):`
* `def test_write(db, data, count):`

Modules used in program: 
* `import leveldb`
* `import random`
* `import time`

## python test leveldb

Python example: test leveldb

```python
import time
import random
import leveldb

Data1 = ' ' * 100
Data2 = ' ' * 10000

def test_write(db, data, count):
    size = 0
    for i in range(count):
        key = str(random.random())
        size += len(key) + len(data)
        db.Put(key, data)
    return size

def timed_call(func, args):
    t1 = time.time()
    res = func(*args)
    t2 = time.time()
    dt = t2 - t1
    return res, dt

def test(data, count):
    db = leveldb.LevelDB('./%sx%s' % (len(data), count))
    totB, dt = timed_call(test_write, [db, data, count])

    totKB = totB / 1024.0
    spd1 = count / dt
    spd2 = totKB / dt
    print('Keys: %d, Data: %.1fKB, Time: %.1fs, Speed: %.1fr/s, %.1fKB/s' % \)
          (count, totKB, dt, spd1, spd2)

test(Data1, 1000)
test(Data2, 1000)
test(Data1, 100000)
test(Data2, 100000)

# Output:
# Keys: 1000, Data: 111.3KB, Time: 0.0s, Speed: 59869.0r/s, 6665.7KB/s
# Keys: 1000, Data: 9779.3KB, Time: 0.3s, Speed: 3222.5r/s, 31513.5KB/s
# Keys: 100000, Data: 11132.9KB, Time: 1.1s, Speed: 88672.9r/s, 9871.8KB/s
# Keys: 100000, Data: 977929.7KB, Time: 402.9s, Speed: 248.2r/s, 2427.1KB/s

# DB size:
# 100x1000/       152K
# 10000x1000/      14M
# 100x100000/      16M
# 10000x100000/   962M


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
