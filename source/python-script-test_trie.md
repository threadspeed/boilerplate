---
title: python script test trie (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test trie'

Functions in program: 
* `def test_make_trie_root_and_nodes():`
* `def create_transactions(count):`

Modules used in program: 
* `import rlp`
* `import random`
* `import pstats`
* `import os`
* `import cProfile`

## python test trie

Python example: test trie

```python
import cProfile
import os
import pstats
import random

import rlp

from eth.db.trie import make_trie_root_and_nodes
from eth.vm.forks.frontier.transactions import FrontierTransaction


def create_transactions(count):
    transactions = []
    for i in range(count):
        value = random.randint(0, 999)
        data = os.urandom(32)
        to = os.urandom(20)
        v, r, s = random.randint(0, 999), random.randint(0, 999), random.randint(0, 999)
        transactions.append(FrontierTransaction(
            nonce=i, gas_price=123, gas=1234000, to=to, value=value, data=data, v=v, r=r, s=s))
    encoded = rlp.encode(transactions)
    return rlp.decode(
        encoded, sedes=rlp.sedes.CountableList(FrontierTransaction), recursive_cache=True)


def test_make_trie_root_and_nodes():
    profiler = cProfile.Profile()
    transactions = create_transactions(10000)
    profiler.enable()
    make_trie_root_and_nodes(transactions)
    profiler.disable()

    stats = pstats.Stats(profiler)
    stats.sort_stats('cumulative').print_stats(30)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
