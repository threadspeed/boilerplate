---
title: python script lambda vs itemgetter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lambda vs itemgetter'

Functions in program: 
* `def test_itemgetter():`
* `def test_lambda():`
* `def random_point():`

Modules used in program: 
* `import timeit`
* `import random`

## python lambda vs itemgetter

Python example: lambda vs itemgetter

```python
import random
from operator import itemgetter
import timeit

def random_point():
    return (random.randint(0, 100), random.randint(0, 100), random.randint(0, 100))

points = None # Global because of timeit scoping

def test_lambda():
    res = map(lambda x: (x[0], x[1]), points)
    return list(res)

def test_itemgetter():
    res = map(itemgetter(0, 1), points)
    return list(res)

if __name__ == '__main__':
    for list_size in [10 ** i for i in range(4)]:
        points = [random_point() for _ in range(list_size)]

        print('For {} points...'.format(list_size))
        print('lambda: ' + str(timeit.timeit('test_lambda()', setup='from __main__ import random_point, test_lambda')))
        print('itemgetter: ' + str(timeit.timeit('test_itemgetter()', setup='from __main__ import test_lambda, test_itemgetter')))

'''
Results when run on my MBP, 2.9GHz i7, 16GB RAM:
? python3 lambda_vs_itemgetter.py
For 1 points...
lambda: 0.6781606969889253
itemgetter: 0.6438146610162221
For 10 points...
lambda: 1.807901046006009
itemgetter: 1.2826563900162
For 100 points...
lambda: 13.209294543979922
itemgetter: 8.561795233021257
For 1000 points...
lambda: 121.1875108690001
itemgetter: 75.26542069698917
For 10000 points...
lambda: 1513.995034438005
itemgetter: 984.4290115500044
'''

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
