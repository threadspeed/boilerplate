---
title: python script 3-avg (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '3-avg'

Functions in program: 
* `def calculate_rating_avg(distancer, users, userId, itemId, max_n):`
* `def get_users_with_item(ratings, itemId):`
* `def read_file(file_path):`

Modules used in program: 
* `import random`
* `import operator`
* `import copy`
* `import pprint`

## python 3-avg

Python example: 3-avg

```python
from math import sqrt
import pprint
import copy
import operator
import random

def read_file(file_path):
    ratings = {}

    with open(file_path) as f:
        lines = f.readlines()

        for line in lines:
            userId, movieId, rating, _ = line.strip().split("\t")

            if userId not in ratings:
                ratings[userId] = {}
            ratings[userId][movieId] = int(rating)

    return ratings

class CosineDistancer:
    def __init__(self):
        self.cache = {}
        self.cache_hits = 0
        self.cache_misses = 0

    def combine_users(self, user1, user2):
        # Make sure we do not modify the original user data set.
        user1 = copy.copy(user1)
        user2 = copy.copy(user2)

        # Get a unique list of the all the keys shared between the users.
        all_keys = set(user1.keys()) | set(user2.keys())

        # Fill in missing values so that they both have the same keys.
        for key in all_keys:
            if key not in user1:
                user1[key] = None
            if key not in user2:
                user2[key] = None

        # Sort by key and only get values that are shared by both users.
        u1 = []
        u2 = []
        for key in sorted(user1.iterkeys()):
            if user1[key] is not None and user2[key] is not None:
                u1.append(user1[key])
                u2.append(user2[key])

        return u1, u2

    def cosine_distance(self, user1, user2):
        # Test the cache first.
        cache_key = '%s:%s' % (user1, user2)
        if cache_key in self.cache:
            self.cache_hits += 1
            return self.cache[cache_key]
        else:
            self.cache_misses += 1

        u1, u2 = self.combine_users(user1, user2)

        top = 0
        user1bottom = 0
        user2bottom = 0

        for i in range(0, len(u1)):
            if u1[i] is not None and u2[i] is not None:
                top += u1[i] * u2[i]
                user1bottom += u1[i] * u1[i]
                user2bottom += u2[i] * u2[i]
     
        bottom = sqrt(user1bottom) * sqrt(user2bottom)
        if bottom == 0:
            self.cache[cache_key] = 0
        else:
            self.cache[cache_key] = top / bottom

        return self.cache[cache_key]

def get_users_with_item(ratings, itemId):
    users = []
    for userId in ratings:
        if itemId in ratings[userId]:
            users.append(userId)

    return users

def calculate_rating_avg(distancer, users, userId, itemId, max_n):
    dist = {}
    for related_user in get_users_with_item(users, itemId):
        if related_user == userId:
            continue

        dist[related_user] = distancer.cosine_distance(users[userId], users[related_user])

    sorted_dist = sorted(dist.items(), key=operator.itemgetter(1), reverse=True)
    total = 0.0
    n = 0
    for i in range(0, max_n):
        try:
            total += users[sorted_dist[i][0]][itemId]
        except:
            break
        n += 1

    if n == 0:
        return 2.5

    return total / n

ratings = read_file('/Users/elliot/Downloads/ml-100k/u1.base')
test_ratings = read_file('/Users/elliot/Downloads/ml-100k/u1.test')
distancer = CosineDistancer()
total = 0
n = 0

print("\tItem ID\tRMSE")
for test_user in test_ratings:
    for itemId in test_ratings[test_user]:
        guess = calculate_rating_avg(distancer, ratings, str(test_user),
            str(itemId), 10)

        real = test_ratings[test_user][itemId]

        diff = real - guess
        total += diff * diff
        n += 1.0
        rmse = sqrt(total / n)

    print('%d\t%s\t%.3f' % (n, itemId, rmse))

print
print('%d cache hits, %d cache misses.' % ()
    distancer.cache_hits, distancer.cache_misses)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
