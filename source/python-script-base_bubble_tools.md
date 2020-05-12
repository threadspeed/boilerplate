---
title: python script base bubble tools (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'base bubble tools'

Functions in program: 
* `def create_undirected_edge(node1, node2):`
* `def bernoulli_sample(p):`

Modules used in program: 
* `import random`

## python base bubble tools

Python example: base bubble tools

```python
import random


def bernoulli_sample(p):
    return 1 if random.uniform(0, 1) < p else 0


class Node:

    def __init__(self):
        self.neighbors = []

    def add_edge(self, node2):
        self.neighbors.append(node2)


def create_undirected_edge(node1, node2):
    node1.add_edge(node2)
    node2.add_edge(node1)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
