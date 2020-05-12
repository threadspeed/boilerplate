---
title: python script redis choc supply (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'redis choc supply'


Modules used in program: 
* `import random`
* `import redis`

## python redis choc supply

Python example: redis choc supply

```python
import redis
import random
from time import sleep

conn = redis.Redis()
chocolates = ['sweet', 'bitter', 'milk', 'white', 'green tea']
while True:
    sleep(random.random())
    chocolate = random.choice(chocolates)
    conn.rpush('chocolates', chocolate)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
