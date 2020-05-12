---
title: python script impl myfunc (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'impl myfunc'

Functions in program: 
* `def remove_key(d, key):`
* `def get_city(file):`
* `def ordered(obj):`

Modules used in program: 
* `import random`

## python impl myfunc

Python mysql example: impl myfunc

```python
import random


def ordered(obj):
    if isinstance(obj, dict):
        return sorted((k, ordered(v)) for k, v in obj.items())
    if isinstance(obj, list):
        return sorted(ordered(x) for x in obj)
    else:
        return obj


def get_city(file):
    import csv
    with open(file) as csv_file:
        csv_reader = csv.reader(csv_file, delimiter=',')
        data = [row for row in csv_reader]
        city = random.choice(data)[0]
        return city


def remove_key(d, key):
    if key in d:
        del d[key]
    return d


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
