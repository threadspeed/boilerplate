---
title: python script list (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'list'

Functions in program: 
* `def dict_opt(d):`
* `def list_opt(l):`

## python list

Python example: list

```python
# -*- coding: utf-8 -*-


def list_opt(l):
    l.append('strawberry')
    l.extend(['watermelon', 'dragon fruit'])
    l.insert(2, 'cucumber')
    print(l)
    print("length: {}".format(len(l)))
    print("cucumber index: {}".format(l.index('cucumber')))

    # cucumber = l.pop('cucumber')
    l.remove('cucumber')
    print("current length: {}".format(len(l)))
    print(", ".join(l))


def dict_opt(d):
    print("d.keys: {}".format(d.keys()))
    print("d.values: {}".format(d.values()))
    for k, v in d.items():
        print("key: {}, value: {}".format(k, v))

    items = [(k, v) for k, v in d.items()]
    print(items)


if __name__ == '__main__':
    list_opt(['apple', 'orange', 'banana'])
    dict_opt({"server": "mpilgrim", "database": "master", "uid": "sa", "pwd": "secret"})

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
