---
title: python script schema1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'schema1'

Functions in program: 
* `def benchmark(users_count=20, items_per_user=10):`
* `def fetch(db, user_count=100):`
* `def fill(db, user_count=100, per_user_items=20):`
* `def get_recommendations(db, user):`
* `def insert(db, user, item):`

Modules used in program: 
* `import pymongo`
* `import random`

## python schema1

Python example: schema1

```python
import random
import pymongo
from pymongo import Connection


def insert(db, user, item):
    db.items.update(
        {'item': item, 'user': user}, {'$set': {'item': item, 'user': user}},
        True
    )
    for current_item in db.items.find({'user': user}):
        current_item = current_item['item']
        db.similarity.update(
            {'item_1': current_item, 'item_2': item},
            {'$set': {'item_1': current_item, 'item_2': item, 'similarity': 1}},
            True
        )
        db.similarity.update(
            {'item_2': current_item, 'item_1': item},
            {'$set': {'item_2': current_item, 'item_1': item, 'similarity': 1}},
            True
        )


def get_recommendations(db, user):
    items = db.items.find({'user': user})
    candidates = {}
    for similar in db.similarity.find(
        {'item_1': {'$in': [i['item'] for i in items]}}
    ):
        candidates.setdefault(similar['item_2'], 0)
        candidates[similar['item_2']] += 1
    result = sorted(
        [{'k': k, 'v': v} for k, v in candidates.items() if k not in [i['item'] for i in items]],
        key=lambda item: item['v'], reverse=True
    )
    #print(result)
    return result


def fill(db, user_count=100, per_user_items=20):
    db.users.drop()
    db.similarity.drop()
    db.items.ensure_index([
        ('user', pymongo.ASCENDING), ('item', pymongo.ASCENDING)
    ])
    db.similarity.ensure_index([
        ('item_1', pymongo.ASCENDING), ('item_2', pymongo.ASCENDING)
    ])
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
    db = connection.test_schema2
    fill(db, users_count, items_per_user)
    fetch(db, users_count)

if __name__ == '__main__':
    benchmark()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
