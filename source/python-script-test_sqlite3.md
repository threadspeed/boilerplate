---
title: python script test sqlite3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test sqlite3'

Functions in program: 
* `def test(data, count):`
* `def timed_call(func, args):`
* `def test_write(db, data, count):`

Modules used in program: 
* `import sqlite3`
* `import random`
* `import time`

## python test sqlite3

Python mysql example: test sqlite3

```python
import time
import random
import sqlite3

Data1 = ' ' * 100
Data2 = ' ' * 10000

def test_write(db, data, count):
    size = 0
    for i in range(count):
        key = str(random.random())
        size += len(key) + len(data)
        cs = db.cursor()
        cs.execute("INSERT INTO kv VALUES('%s', '%s')" % (key, data))
        db.commit()
    return size

def timed_call(func, args):
    t1 = time.time()
    res = func(*args)
    t2 = time.time()
    dt = t2 - t1
    return res, dt

def test(data, count):
    db = sqlite3.connect('%sx%s.db' % (len(data), count))
    cs = db.cursor()
    cs.execute('CREATE TABLE kv(name text UNIQUE, value text)')

    totB, dt = timed_call(test_write, [db, data, count])
    db.close()

    totKB = totB / 1024.0
    spd1 = count / dt
    spd2 = totKB / dt
    print('Keys: %d, Data: %.1fKB, Time: %.1fs, Speed: %.1fr/s, %.1fKB/s' % \)
          (count, totKB, dt, spd1, spd2)


test(Data1, 1000)
test(Data2, 1000)

# Output:
# Keys: 1000, Data: 111.3KB, Time: 72.0s, Speed: 13.9r/s, 1.5KB/s
# Keys: 1000, Data: 9779.3KB, Time: 121.1s, Speed: 8.3r/s, 80.7KB/s

# DB size;
# 100x1000.db      152K
# 10000x1000.db    9.8M


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
