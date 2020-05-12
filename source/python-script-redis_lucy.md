---
title: python script redis lucy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'redis lucy'


Modules used in program: 
* `import random`
* `import redis`

## python redis lucy

Python mysql example: redis lucy

```python
import redis
from time import sleep
from datetime import datetime
import random

conn = redis.Redis()
print('Lucy is ready...')
timeout = 20
while True:
    sleep(0.5)
    msg = conn.blpop('chocolates', timeout)
    remaining = conn.llen('chocolates')
    if msg:
        chocolate = msg[1]
        print("Lucy got a", chocolate, "at", datetime.now(), ". Still remaining", remaining, "pieces")



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
