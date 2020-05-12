---
title: python script bk tree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bk tree'

Functions in program: 
* `def distance(str1: str, str2: str):`

Modules used in program: 
* `import random`

## python bk tree

Python example: bk tree

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Author: ficapy
# Create: '03/03/2018'

import random
from string import ascii_lowercase


def distance(str1: str, str2: str):
    return sum(str1[i] != str2[i] for i in range(len(str1)))


class Node:
    def __init__(self, content: str, child: dict):
        self.content = content
        self.child = child


class BKTree:
    def __init__(self, init_content: str):
        self.root = Node(init_content, {})

    def insert(self, content: str):
        d = distance(content, self.root.content)
        node = Node(content, {})
        if d not in self.root.child:
            self.root.child[d] = node
            return
        else:
            origin = self.root
            self.root = self.root.child[d]
            self.insert(content)
            self.root = origin

    def search(self, target, k, result=[]):
        # 距离小于等于K的
        x = distance(target, self.root.content)
        if x <= k:
            result.append(self.root.content)
        for i, _ in self.root.child.items():
            if i <= x + k:
                origin = self.root
                self.root = self.root.child[i]
                self.search(target, k)
                self.root = origin
        return result


ori = list(set([''.join(random.choice(ascii_lowercase) for _ in range(4)) for _ in range(100)]))

bk = BKTree("abcd")
for i in ori:
    bk.insert(i)

bk_result = bk.search(ori[0], 2)

general_ret = []
for i in ori:
    if distance(i, ori[0]) <= 2:
        general_ret.append(i)

print(bk_result)
print(general_ret)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
