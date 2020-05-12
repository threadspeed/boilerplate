---
title: python script 1-random (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '1-random'

Functions in program: 
* `def read_file(file_path):`

Modules used in program: 
* `import random`
* `import pprint`

## python 1-random

Python mysql example: 1-random

```python
from math import sqrt
import pprint
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

# So our "randoms" are always the same.
random.seed(0)

test_ratings = read_file('ml-100k/u1.test')
total = 0
n = 0

print("\tItem ID\tRMSE")
for test_user in test_ratings:
    for itemId in test_ratings[test_user]:
        guess = random.randint(1, 5)
        real = test_ratings[test_user][itemId]

        diff = real - guess
        total += diff * diff
        n += 1.0
        rmse = sqrt(total / n)

    print('%d\t%s\t%.3f' % (n, itemId, rmse))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
