---
title: python script quicksort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quicksort'

Functions in program: 
* `def quicksort(array):`
* `def _quicksort(array, lower, upper):`
* `def _partition(array, lower, upper):`
* `def _swap(array, i, j):`

Modules used in program: 
* `import unittest`

## python quicksort

Python mysql example: quicksort

```python
'''Quicksort implementation according to CLRS'''

import unittest

def _swap(array, i, j):
    tmp = array[i]
    array[i] = array[j]
    array[j] = tmp

def _partition(array, lower, upper):
    pivot = array[upper]
    splitter = lower - 1

    for end in xrange(lower, upper):
        if array[end] <= pivot:
            splitter += 1
            _swap(array, splitter, end)

    _swap(array, splitter + 1, upper)
    return splitter + 1

def _quicksort(array, lower, upper):
    if lower >= upper: return
    pivot_pos = _partition(array, lower, upper)
    _quicksort(array, lower, pivot_pos - 1)
    _quicksort(array, pivot_pos + 1, upper)

def quicksort(array):
    _quicksort(array, 0, len(array)-1)
    return array

class QuickSortTestClass(unittest.TestCase):
    def test_100(self):
        array = [1,2,3,4,5]
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_200(self):
        array = [3,1,4,9,3]
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_300(self):
        array = []
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_400(self):
        array = [1,1,1,1]
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_500(self):
        array = [1]
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_600(self):
        array = [1,2,3,4,5]
        self.assertEqual(
                sorted(array),
                quicksort(array))

    def test_700(self):
        import random
        for i in xrange(100):
            # build a random array
            length = random.randint(0,1000)
            array = []
            for j in xrange(length):
                array.append(random.randint(0,1000))

            # test
            self.assertEqual(
                    sorted(array),
                    quicksort(array))

if __name__ == "__main__":
    unittest.main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
