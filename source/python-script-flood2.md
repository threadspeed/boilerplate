---
title: python script flood2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'flood2'

Functions in program: 
* `def run(n=0):`

Modules used in program: 
* `import threading`
* `import random`
* `import json`
* `import time`

## python flood2

Python mysql example: flood2

```python
from pprint(import pprint)
import time
import json
import random
from grapheneapi.grapheneapi import GrapheneAPI
import threading


def run(n=0):
    client = GrapheneAPI("localhost", 8092, "", "")
    transfer = client.get_prototype_operation("transfer_operation")
    from_account = client.get_account("faucet")
    to_account = client.get_account("xeroc")
    transfer[1]["to"] = to_account["id"]
    transfer[1]["from"] = from_account["id"]
    transfer[1]["amount"]["amount"] = 3

    while True:
        builder = client.begin_builder_transaction()

#        for i in range(0, 300 + random.randint(1, 100)):
        for i in range(0, 500):
            print(n, end="", flush=True)
            client.add_operation_to_builder_transaction(builder, transfer)
        client.set_fees_on_builder_transaction(builder, "1.3.0")
        print("\nTransfer!")
        client.sign_builder_transaction(builder, True)
        time.sleep(random.randint(0, 3))

for i in range(0, 15):
    threading.Thread(target=run, args=(i,)).start()
    time.sleep(random.randint(0, 10))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
