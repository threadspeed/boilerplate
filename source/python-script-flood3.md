---
title: python script flood3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'flood3'

Functions in program: 
* `def flooder(n=0):`
* `def run(port, n=0):`
* `def kill(proc):`
* `def wallet(port):`

Modules used in program: 
* `import subprocess`
* `import random`
* `import json`
* `import time`
* `import threading`
* `import psutil`

## python flood3

Python example: flood3

```python
import psutil
import threading
import time
import json
import random
from grapheneapi.grapheneapi import GrapheneAPI
import subprocess


def wallet(port):
    print("Starting new wallet on port %d" % port)
    proc = subprocess.Popen([
        "/home/xeroc/BitShares/testnet/testnet/programs/cli_wallet/cli_wallet",
        "--server-rpc-endpoint=wss://node.testnet.bitshares.eu",
        "--rpc-http-endpoint=127.0.0.1:%d" % port,
        "--wallet-file=/home/xeroc/BitShares/testnet/testnet/wallet.json",
        "--daemon"
    ])
    return proc


def kill(proc):
    proc.terminate()


def run(port, n=0):
    client = GrapheneAPI("localhost", port)
    client.unlock("password")
    transfer = client.get_prototype_operation("transfer_operation")
    from_account = client.get_account("faucet")
    to_account = client.get_account("xeroc")
    transfer[1]["to"] = to_account["id"]
    transfer[1]["from"] = from_account["id"]
    transfer[1]["amount"]["amount"] = 1 + n

    while True:
        builder = client.begin_builder_transaction()

        for i in range(0, 200 + random.randint(0, 100)):
            print(n, end="", flush=True)
            client.add_operation_to_builder_transaction(builder, transfer)
        client.set_fees_on_builder_transaction(builder, "1.3.0")
        print("\nTransfer!")
        client.sign_builder_transaction(builder, True)
        time.sleep(random.randint(0, 3))


def flooder(n=0):
    port = 9900 + n
    p = wallet(port)

    time.sleep(15 + random.randint(0, 5))
    run(port, n)

    print("sleep 10")
    time.sleep(10)
    kill(p)


for i in range(0, 5):
    threading.Thread(target=flooder, args=(i,)).start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
