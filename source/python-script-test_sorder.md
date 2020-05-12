---
title: python script test sorder (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test sorder'


Modules used in program: 
* `import sorter`
* `import random`

## python test sorder

Python mysql example: test sorder

```python
import random
from unittest import TestCase

from nose.tools import istest

import sorter


class SorterTest(TestCase):
    @istest
    def sorts_simple_list(self):
        """Sorts a simple list"""
        some_list = [3, 1, 2]
        sorter.sort(some_list)

        self.assertEqual(some_list, [1, 2, 3])

    @istest
    def sorts_a_bigger_list(self):
        """Sorts a somewhat bigger list"""
        some_list = [5, 7, 3, 8, 9]
        sorter.sort(some_list)

        self.assertEqual(some_list, [3, 5, 7, 8, 9])

    @istest
    def sorts_a_huge_list(self):
        """Sorts a huge list"""
        num_elements = 100
        some_list = range(num_elements)
        random.shuffle(some_list)
        sorter.sort(some_list)

        self.assertEqual(some_list, list(range(num_elements)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
