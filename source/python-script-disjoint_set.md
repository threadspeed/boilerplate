---
title: python script disjoint set (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'disjoint set'


Modules used in program: 
* `import random`

## python disjoint set

Python example: disjoint set

```python
"""disjoint_set.py
"""


import random


class DisjointSet(object):
    """DisjointSet

    A Disjoint-Set data structure (also called Union–Find or Merge–Find
    set) is a data structure that tracks a set of elements partitioned
    into a number of disjoint (non-overlapping) subsets.  It supports
    2 operations:

    * "find": determine which subset a particular element is in.  This
              can be used for determining if two elements are in the
              same subset.
    * "union": join two subsets into a single subset.
    """

    def __init__(self, size):
        """__init__

        # Arguments
            size: int, total number of elements in the disjoint set.
                  Each element is id'ed as 0, 1, ..., (size-1).  When
                  the disjoint set is instantiated, all elements are
                  "disjoint" (each in its own subset).
        """
        self._size = size
        self._parent = list(range(size))

    def find(self, x):
        if self._parent[x] == x:
            return x
        else:
            return self.find(self._parent[x])

    def union(self, x, y):
        xset = self.find(x)
        yset = self.find(y)
        if random.random() < 0.5:
            self._parent[xset] = yset
        else:
            self._parent[yset] = xset

    def __repr__(self):
        finds = [self.find(i) for i in range(self._size)]
        return str({f: [i for i, s in enumerate(finds) if s == f]
                    for f in set(finds)})

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
