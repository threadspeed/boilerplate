---
title: python script get ranking data (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'get ranking data'

Functions in program: 
* `def ranking_redis(r, key):`
* `def ranking_sqlite(conn, key):`

Modules used in program: 
* `import random`
* `import random`
* `import sys`
* `import redis`
* `import sqlite3`

## python get ranking data

Python example: get ranking data

```python
import sqlite3
import redis
import sys
from timeit import Timer

loop = int(sys.argv[1])

def ranking_sqlite(conn, key):
    cur = conn.cursor()
    cur.execute("SELECT val FROM ranking WHERE key = '%s' ORDER BY score DESC limit 10" % key)
    vals = [row[0] for row in cur]
    cur.close()
    #print(vals)

def ranking_redis(r, key):
    vals = [val for val in r.zrevrange(key, 0, 9)]
    # print(vals)

    
setup1 = """
import random
from __main__ import ranking_sqlite, conn
"""
stmt1 = """
key = '%08d' % random.randint(0, 100000)
ranking_sqlite(conn, key)
"""
setup2 = """
import random
from __main__ import ranking_redis, r
"""
stmt2 = """
key = '%08d' % random.randint(0, 100000)
ranking_redis(r, key)
"""

loop = int(sys.argv[1])

conn = sqlite3.connect('data.db')
t = Timer(stmt1, setup1)
print('SQLite (loop=%d)' % loop)
print(t.timeit(loop))
conn.close()

r = redis.Redis(host='localhost', port=6379)
t = Timer(stmt2, setup2)
print('Redis (loop=%d)' % loop)
print(t.timeit(loop))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
