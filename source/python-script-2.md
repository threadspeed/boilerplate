---
title: python script 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '2'

Functions in program: 
* `def loadlist():`

Modules used in program: 
* `import timeit`
* `import random`

## python 2

Python mysql example: 2

```python
#import profile
import random
import timeit


class Node(object):
    __slots__ = ('value', 'next')

    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

    def __str__(self):
        return self.value.__str__()


class LIIter(object):
    __slots__ = ('lst', 'current')

    def __init__(self, lst):
        self.lst = lst
        self.current = self.lst.first

    def __iter__(self):
        return self

    def next(self):
        r = self.current
        if r is None:
            raise StopIteration
        self.current = r.next
        return r


class LinkedList(object):
    __slots__ = ('first', 'last', 'length', 'ins', 'old', 'curr',
        'insert', 'items')

    def __init__(self):
        self.first = None
        self.last = None
        self.length = 0
        self.ins = 0
        self.old = None
        self.curr = None
        self.insert = self.insert_zero
        self.items = set()

    def __iter__(self):
        return LIIter(self)

    def __str__(self):
        l = []
        for x in self:
            l.append(str(x))
        return 'LinkedList = {0}'.format(', '.join(l))

    def insert_zero(self, somevalue):
        self.items.add(somevalue)
        self.first = self.last = Node(somevalue, None)
        self.insert = self.insert_nonzero

    def insert_nonzero(self, somevalue):
        if somevalue in self.items:
            return
        if self.first.value > somevalue:
            self.first = Node(somevalue, self.first)
        elif self.last.value < somevalue:
            self.last.next = Node(somevalue, None)
            self.last = self.last.next
        else:
            old = self.first
            for curr in self:
                if curr.value > somevalue:
                    old.next = Node(somevalue, curr)
                    break
                old = curr
        self.items.add(somevalue)


def loadlist():
    L = LinkedList()
    for i in range(0, 2500):
        L.insert(int(random.uniform(0, 100)))

if __name__ == '__main__':
    t = timeit.Timer('loadlist()', 'from __main__ import loadlist')
    print(t.timeit(10))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
