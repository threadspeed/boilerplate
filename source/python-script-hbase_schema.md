---
title: python script hbase schema (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hbase schema'

Functions in program: 
* `def benchmark(users_count=20, items_per_user=10):`
* `def fetch(db, user_count=100):`
* `def fill(db, user_count=100, per_user_items=20):`
* `def get_recommendations(db, user):`
* `def insert(db, user, item):`

Modules used in program: 
* `import pymongo`
* `import random`

## python hbase schema

Python mysql example: hbase schema

```python
# Bonus: my very poor hbase test

import random
import pymongo
from pyhbase.connection import HBaseConnection


connection = HBaseConnection('127.0.0.1', port=9090)
if connection.table_exists('users'):
    connection.drop('users')
connection.create_table('users', 'info', 'items')
if connection.table_exists('similarity'):
    connection.drop('similarity')
connection.create_table('similarity', 'similar')


def insert(db, user, item):
    connection.put('users', str(user), 'items:%s' % item, str(1))
    current_user = connection.get('users', str(user))
    for entry in current_user['entries']:
        current_item = entry['qualifier']
        connection.put(
            'similarity', str(current_item), 'similar:%s' % item, str(1)
        )
        connection.put(
            'similarity', str(item), 'similar:%s' % current_item, str(1)
        )


def get_recommendations(db, user):
    current_user = connection.get('users', str(user))
    candidates = {}
    current_user_items = [i['qualifier'] for i in current_user['entries']]
    for current_item in current_user_items:
        items = connection.get('similarity', str(current_item))
        for similar in items['entries']:
            candidates.setdefault(similar['qualifier'], 0)
            candidates[similar['qualifier']] += 1
        result = sorted(
            [{'k': k, 'v': v} for k, v in candidates.items() if k not in current_user_items],
            key=lambda item: item['v'], reverse=True
        )
    #print(result)
    return result


def fill(db, user_count=100, per_user_items=20):
    for i in xrange(user_count):
        for t in xrange(per_user_items):
            item = random.randrange(i, i+10)
            #print('Adding user %d and item %d...' % (i, item))
            insert(db, i, item)


def fetch(db, user_count=100):
    for user in xrange(user_count):
        recommendations = get_recommendations(db, user)

def benchmark(users_count=20, items_per_user=10):
    db = 'test_schemah'
    print('Initialized')
    fill(db, users_count, items_per_user)
    fetch(db, users_count)

if __name__ == '__main__':
    benchmark()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
