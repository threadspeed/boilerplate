---
title: python script Life (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Life'


Modules used in program: 
* `import random`

## python Life

Python example: Life

```python
# -*- coding: utf-8 -*-

"""Life.py

生命类
"""

import random


class Life(object):

    def __init__(self, env, gene=None):
        self.env = env
        self.score = 0

        if gene is None:
            self.__rnd_gene()
        elif isinstance(gene, list):
            self.gene = []
            for k in gene:
                self.gene.append(k)
        else:
            self.gene = gene

    def __rnd_gene(self):
        self.gene = ""
        for i in range(self.env.gene_length):
            self.gene += str(random.randint(0, 1))

    def set_score(self, v):
        self.score = v

    def add_score(self, v):
        self.score += v


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
