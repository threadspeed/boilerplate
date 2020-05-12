---
title: python script conftest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'conftest'

Functions in program: 
* `def pytest_collection_modifyitems(items):`

Modules used in program: 
* `import random`

## python conftest

Python mysql example: conftest

```python
import random

def pytest_collection_modifyitems(items):
    random.shuffle(items)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
