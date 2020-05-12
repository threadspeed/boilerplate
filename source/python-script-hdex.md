---
title: python script hdex (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hdex'


Modules used in program: 
* `import random`
* `import leveldb`
* `import random`
* `import hyperclient`

## python hdex

Python mysql example: hdex

```python
#hyperdex

import hyperclient
import random
c = hyperclient.Client('127.0.0.1', 1982)

for i in range(100000):
        pre = random.choice("abcdefghijklmnopqrstuvwxyz")
        id = pre + "neo" + str(i)
        c.put('phonebook', id, {'first': 'Somemore', 'last': 'COOOOL', 'phone': 6075551024})

#leveldb
import leveldb
import random

db = leveldb.LevelDB("/home/srini/hdex/db/leveldb")

for i in range(100000):
        pre = random.choice("abcdefghijklmnopqrstuvwxyz")
        id = pre + "neo" + str(i)
        db.Put(id, "Some string - some more string")
        
        

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
