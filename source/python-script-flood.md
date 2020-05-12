---
title: python script flood (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'flood'


Modules used in program: 
* `import random`
* `import json`
* `import time`

## python flood

Python example: flood

```python
import time
import json
import random
from grapheneapi.grapheneapi import GrapheneAPI

if __name__ == '__main__':
    client = GrapheneAPI("localhost", 8092, "", "")
    while True:
        for i in range(0, random.randint(1, 100)):
            print(i)
            res = client.transfer("faucet", "init0", "0.00007", "TEST", "", True)
        time.sleep(random.randint(0, 3))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
