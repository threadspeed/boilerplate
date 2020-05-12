---
title: python script make data redis (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'make data redis'


Modules used in program: 
* `import random`
* `import uuid`
* `import redis`

## python make data redis

Python mysql example: make data redis

```python
import redis
import uuid
import random

r = redis.Redis(host='localhost', port=6379)
for i in range(100000):
    key = '%08d' % i
    for j in range(random.randint(1, 50)):
        val = str(uuid.uuid4())
        score = random.randint(1, 100)
        r.zadd(key, val, score)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
