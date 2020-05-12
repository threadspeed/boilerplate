---
title: python script 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '1'

Functions in program: 
* `def loadlist():`

Modules used in program: 
* `import timeit`
* `import random`

## python 1

Python mysql example: 1

```python
import random
import timeit


class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next


class LinkedList:
    def __init__(self):
        self.first = None
        self.last = None
        self.length = 0
        self.ins = 0
        self.old = None
        self.curr = None
        self.items = set()

    def RemoveDuplicates(self):
        if (self.first == None):
            return
        old = curr = self.first
        while curr != None:
            _del = 0
            if curr.next != None:
                if curr.value == curr.next.value:
                    curr.next = curr.next.next
                    _del = 1
            if _del == 0:
                curr = curr.next

    def __str__(self):
        if self.first != None:
            current = self.first
            out = 'LinkedList = ' + str(current.value) + ' '
            while current.next != None:
                current = current.next
                out += str(current.value) + ' '
            return out + ''
        return ''


def loadlist():
    L = LinkedList()
    for i in range(0, 2500):
        _r = int(random.uniform(0, 100))
        if _r in L.items:
            continue
        if L.first == None:
            L.first = Node(i, None)
        elif L.first.value > _r:
            L.first = Node(_r, L.first)
        else:
            L.old = L.curr = L.first
            L.ins = 0
            while L.curr != None:
                if L.curr.value > _r:
                    L.curr = Node(_r, L.curr)
                    L.old.next = L.curr
                    L.items.add(_r)
                    L.ins = 1
                    break
                L.old = L.curr
                L.curr = L.curr.next
            if L.ins == 0:
                L.curr = Node(_r, None)
                L.old.next = L.curr
                L.items.add(_r)

    #L.RemoveDuplicates()

if __name__ == '__main__':
    t = timeit.Timer('loadlist()', "from __main__ import loadlist")
    print(t.timeit(10))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
