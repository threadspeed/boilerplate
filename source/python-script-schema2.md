---
title: python script schema2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'schema2'

Functions in program: 
* `def benchmark(users_count=20, items_per_user=10):`
* `def fetch(db, user_count=100):`
* `def fill(db, user_count=100, per_user_items=20):`
* `def get_recommendations(db, user):`
* `def insert(db, user, item):`

Modules used in program: 
* `import pymongo`
* `import random`

## python schema2

Python example: schema2

```python
import random
import pymongo
from pymongo import Connection


def insert(db, user, item):
    db.users.update({'user': user}, {'$set': {'user': user, 'items.%s' % item: 1}}, True)
    current_user = db.users.find_one({'user': user})
    for current_item, current_mark in current_user['items'].items():
        db.similarity.update(
            {'item_1': current_item},
            {'$set': {'similar.%s' % item: 1}},
            True
        )
        db.similarity.update(
            {'item_1': item},
            {'$set': {'similar.%s' % current_item: 1}},
            True
        )


def get_recommendations(db, user):
    current_user = db.users.find_one({'user': user})
    candidates = {}
    for similar in db.similarity.find(
        {'item_1': {'$in': current_user['items'].keys()}}
    ):
        for item_2, v in similar['similar'].items():
            candidates.setdefault(item_2, 0)
            candidates[item_2] += 1
    result = sorted(
        [{'k': k, 'v': v} for k, v in candidates.items() if k not in current_user['items']],
        key=lambda item: item['v'], reverse=True
    )
    #print(result)
    return result


def fill(db, user_count=100, per_user_items=20):
    db.users.drop()
    db.similarity.drop()
    db.users.ensure_index('user')
    db.similarity.ensure_index('item_1')
    for i in xrange(user_count):
        for t in xrange(per_user_items):
            item = random.randrange(i, i+10)
            #print('Adding user %d and item %d...' % (i, item))
            insert(db, i, item)


def fetch(db, user_count=100):
    for user in xrange(user_count):
        recommendations = get_recommendations(db, user)

def benchmark(users_count=20, items_per_user=10):
    connection = Connection()
    db = connection.test_schema3
    fill(db, users_count, items_per_user)
    fetch(db, users_count)

if __name__ == '__main__':
    benchmark()
    

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
