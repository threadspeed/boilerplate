---
title: python script product1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'product1'

Functions in program: 
* `def on_send_success(record_metadata):`

Modules used in program: 
* `import random`

## python product1

Python mysql example: product1

```python
from time import sleep
from json import dumps
from kafka import KafkaProducer
import random

def on_send_success(record_metadata):
    print(record_metadata.__dict__)

producer = KafkaProducer(bootstrap_servers=['localhost:9092'],
                         value_serializer=lambda x: 
                         dumps(x).encode('utf-8'))


while True:
  producer.send('numtest1', value={'number' : random.randrange(0, 100)}).add_callback(on_send_success)
  sleep(1)
producer.flush()
producer = KafkaProducer(retries=5)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
