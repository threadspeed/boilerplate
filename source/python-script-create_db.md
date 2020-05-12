---
title: python script create db (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create db'

Functions in program: 
* `def generateValues(start=0):`

Modules used in program: 
* `import random`
* `import sqlite3`

## python create db

Python example: create db

```python
#!/usr/bin/python

# Generates the sqlite database with 1 mil rows (runs for 30s or so)

import sqlite3
import random

conn = sqlite3.connect('test.db')

c = conn.cursor()

c.execute('''CREATE TABLE IF NOT EXISTS plot \
        (x integer, y real, x_bound, type text, message text)''')
c.execute('''CREATE INDEX IF NOT EXISTS index_x_bound \
        ON plot (x_bound)''')
# c.execute('''CREATE INDEX IF NOT EXISTS index_x ON plot (index_x)''')

conn.commit()


N = 1000000
BATCH_SIZE = 100
START_TIME = 140693811

def generateValues(start=0):
    depl = 0
    while True:
        # Time variation
        x = START_TIME + start + depl
        # x reference value we need
        x_bound = round(x / 10)
        # y is random
        y = random.random() * 100
        messageType = 'Type_' + str(random.randint(0, 250))
        message = 'Message ' + str(x)
        yield (x, y, x_bound, messageType, message)
        depl += 1  # random.randint(0, 10)


gen = generateValues()
for x in xrange(0, N / BATCH_SIZE):
    c.executemany('INSERT INTO plot VALUES (?, ?, ?, ?, ?)',
                  [next(gen) for x in xrange(0, BATCH_SIZE)])
    conn.commit()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
