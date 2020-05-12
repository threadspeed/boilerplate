---
title: python script make data sqlite (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'make data sqlite'


Modules used in program: 
* `import random`
* `import uuid`

## python make data sqlite

Python example: make data sqlite

```python
import uuid
import random

conn = sqlite3.connect('data.db')
cur = conn.cursor()
for i in range(100000):
    key = '%08d' % i
    for j in range(random.randint(1, 50)):
        val = str(uuid.uuid4())
        score = random.randint(1, 100)
        cur.execute('INSERT INTO ranking VALUES (?,?,?)', (key, val, score))
    conn.commit()
cur.close()
conn.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
