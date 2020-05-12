---
title: python script ShuffleQueue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ShuffleQueue'


Modules used in program: 
* `import sys`
* `import random`
* `import collections`

## python ShuffleQueue

Python mysql example: ShuffleQueue

```python
# repeat a list, randomly shuffling after each full pass
# to preserve the original ordering, I tend to store a list of indices:
# ShuffleQueue(range(len(my_other_list)))

import collections
import random
import sys

class ShuffleQueue(collections.UserList):
    def __init__(self,l,rand=random):
        self.container = list(l)
        self.counter = len(self.container)
        self.rand=rand
        self._epoch = 0

    def __iter__(self):
        return self

    def __len__(self):
        return len(self.container) - self.counter

    def __next__(self):
        if len(self) <= 0:
            self.counter = 0
            self.rand.shuffle(self.container)
            self._epoch += 1
        
        result = self.container[self.counter]
        self.counter += 1
        return result

    @property
    def epoch(self):
        return self._epoch


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
