---
title: python script quicksort2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quicksort2'

Functions in program: 
* `def quicksort(array):`
* `def _quicksort(array, lower, upper):`
* `def _partition(array, lower, upper):`
* `def _swap(array, i, j):`

Modules used in program: 
* `import unittest`

## python quicksort2

Python example: quicksort2

```python
'''Quicksort. The implementation of the partition function is different than CLRS'''

import unittest

def _swap(array, i, j):
    tmp = array[i]
    array[i] = array[j]
    array[j] = tmp

def _partition(array, lower, upper):
    assert lower <= upper
    pivot = array[upper]
    pivot_pos = upper
    upper -= 1
    while lower < upper:
        if array[lower] > pivot:
            _swap(array, lower, upper)
            upper -= 1
        else:
            lower += 1
    assert lower == upper
    if array[lower] > pivot:
        _swap(array, lower, pivot_pos)
        return lower
    _swap(array, lower + 1, pivot_pos)
    return lower + 1

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
