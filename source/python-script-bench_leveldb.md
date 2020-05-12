---
title: python script bench leveldb (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bench leveldb'

Functions in program: 
* `def create_random_db(data_path="bench.db", marshal_fun=None, num=100000):`
* `def create_simple_db(data_path="bench.db", marshal_fun=None, num=100000):`
* `def clear_db(data_path):`
* `def base_marshal(x):`
* `def pickle_marshal(x):`
* `def setup_db(data_path):`

Modules used in program: 
* `import plyvel`
* `import random`
* `import ctypes`
* `import random`
* `import pickle`
* `import plyvel`
* `import uuid`

## python bench leveldb

Python example: bench leveldb

```python
import uuid
import plyvel
import pickle
import random


def setup_db(data_path):
    # import plyvel
    return plyvel.DB(data_path, create_if_missing=True)

def pickle_marshal(x):
    return pickle.dumps(x)

def base_marshal(x):
    return b'%d' % x

def clear_db(data_path):
    import shutil
    import os
    if os.path.exists(data_path):
        shutil.rmtree(data_path)

def create_simple_db(data_path="bench.db", marshal_fun=None, num=100000):
    clear_db(data_path)
    db = setup_db(data_path)
    x = 0
    batch_size = 1000
    for _ in range(0, num, batch_size):
        with db.write_batch() as wb:
            for _ in xrange(batch_size):
                key = marshal_fun(x)
                x += 1
                wb.put(key, uuid.uuid4().hex)
    return db


def create_random_db(data_path="bench.db", marshal_fun=None, num=100000):
    clear_db(data_path)
    # import numpy as np
    import ctypes

    db = setup_db(data_path)
    querys = []
    batch_size = 1000
    for _ in range(0, num, batch_size):
        with db.write_batch() as wb:
            for _ in xrange(batch_size):
                x = random.randint(1, ctypes.c_uint(-1).value)
                # x = np.random.randint(0, ctypes.c_uint(-1).value)
                key = marshal_fun(x)
                querys.append(key)
                wb.put(key, uuid.uuid4().hex)

    return db, querys

data_path = "bench.db"
marshal_fun = pickle_marshal

print('init db ...')
# db, rand_querys = create_random_db(data_path, marshal_fun)
# rand_query_keys = rand_querys[:9999]
# base_query_keys = sorted(rand_query_keys)

db = create_simple_db(data_path, marshal_fun, 1000000)
import ctypes
rand_query_keys = [marshal_fun(random.randint(1, ctypes.c_uint(-1).value)) for _ in xrange(9999)]
base_query_keys = [marshal_fun(_) for _ in xrange(9999)]
print('done!')

if __name__ == '__main__':

    import timeit

    # code snippet to be executed only once
    SETUP_CODE = '''
import random
import plyvel
from __main__ import db, base_query_keys, rand_query_keys
'''

    BASE_GET_TEST_CODE = '''
map(lambda x: db.get(x), base_query_keys)'''

    # code snippet whose execution time is to be measured
    RANDOM_GET_TEST_CODE = '''
map(lambda x: db.get(x), rand_query_keys)'''

    # timeit statement
    print(timeit.timeit(setup=SETUP_CODE, stmt=BASE_GET_TEST_CODE, number=5000))
    # clear_db(data_path)
    print(timeit.timeit(setup=SETUP_CODE, stmt=RANDOM_GET_TEST_CODE, number=5000))
    # clear_db(data_path)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
