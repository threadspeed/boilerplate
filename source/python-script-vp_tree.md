---
title: python script vp tree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vp tree'

Functions in program: 
* `def distance(str1: str, str2: str):`

Modules used in program: 
* `import random`

## python vp tree

Python mysql example: vp tree

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
    def __init__(self, content: str, left: str, right: str):
        self.content = content
        self.left = left
        self.right = right
        self.radius = int(len(content) / 2)


class VPTree:
    def __init__(self, init_content: str):
        self.root = Node(init_content, None, None)

    def insert(self, content: str):
        d = distance(self.root.content, content)
        node = Node(content, None, None)
        if d <= self.root.radius:
            if self.root.left is None:
                self.root.left = node
            else:
                origin = self.root
                self.root = self.root.left
                self.insert(content)
                self.root = origin
        else:
            if self.root.right is None:
                self.root.right = node
            else:
                origin = self.root
                self.root = self.root.right
                self.insert(content)
                self.root = origin

    def search(self, target, k, result=[]):
        # 距离小于等于K的
        x = distance(target, self.root.content)
        if x <= k:
            result.append(self.root.content)

        if self.root.radius > (x + k) and (self.root.left is not None):
            origin = self.root
            self.root = self.root.left
            self.search(target, k)
            self.root = origin
        else:
            origin = self.root
            self.root = self.root.left
            if self.root is not None:
                self.search(target, k)
            self.root = origin

            self.root = self.root.right
            if self.root is not None:
                self.search(target, k)
            self.root = origin
        return result


ori = list(set([''.join(random.choice(ascii_lowercase) for _ in range(4)) for _ in range(100)]))

vp = VPTree("abcd")
for i in ori:
    vp.insert(i)
vp_result = vp.search(ori[0], 2)

general_ret = []
for i in ori:
    if distance(i, ori[0]) <= 2:
        general_ret.append(i)

print(vp_result)
print(general_ret)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
