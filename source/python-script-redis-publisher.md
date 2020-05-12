---
title: python script redis-publisher (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'redis-publisher'


Modules used in program: 
* `import random`
* `import threading`
* `import gevent`

## python redis-publisher

Python example: redis-publisher

```python
from redis import Redis
from redis_hashring import RingNode
import gevent
import threading
import random
N_KEYS = 10

if __name__ == "__main__":
    redis = Redis()

    for key in range(N_KEYS):
        redis.rpush(str(key), {'key'+str(key):'value'})
    print('publishing complete.')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
