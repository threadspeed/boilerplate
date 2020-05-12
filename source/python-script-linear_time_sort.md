---
title: python script linear time sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'linear time sort'

Functions in program: 
* `def test_bucket_sort():`
* `def bucket_sort(arr):`
* `def test_radix_sort():`
* `def radix_sort(arr):`

## python linear time sort

Python mysql example: linear time sort

```python
def radix_sort(arr):
    r = 8
    a = 32
    m = (1 << r) - 1

    for sh in range(0, a, r):
        bucket = [[] for _ in range(1 << r)]
        for x in arr:
            ib = (x >> sh) & m
            bucket[ib].append(x)
        arr = []
        for e in bucket:
            arr.extend(e)
    return arr


def test_radix_sort():
    import random
    MAX_INT = (1 << 32) - 1
    N = 300
    arr = [random.randint(0, MAX_INT) for _ in range(N)]
    out = radix_sort(arr)
    for i in range(N - 1):
        assert out[i] <= out[i + 1]


def bucket_sort(arr):
    assert(all(0 <= a < 1 for a in arr))
    
    n = len(arr)
    class ListNode:
        def __init__(self, x):
            self.val = x
            self.next = None

        def __str__(self):
            if self.next:
                return "{} -> {}".format(self.val, self.next)
            else:
                return "{}".format(self.val)
    bkt = [ListNode(-1) for _ in range(n)] 
    
    dx = 1.0 / n
    for x in arr:
        i = int(x / dx)
        i = n - 1 if i >= n else i

        prev = bkt[i]
        node = prev.next
        while True:
            if node is None:
                prev.next = ListNode(x)
                break
            elif x < node.val:
                prev.next = ListNode(x)
                prev.next.next = node
                break
            else:
                prev = node
                node = node.next
            
    out = []
    for prev in bkt:
        node = prev.next
        print(node)
        while node:
            out.append(node.val)
            node = node.next
    return out


def test_bucket_sort():
    import random
    
    n = 1000
    arr = [random.uniform(0.0, 1.0) for _ in range(n)]
    #arr = [(i / n) ** 2 for i in range(n)]
    out = bucket_sort(arr)
    assert(len(out) == n)
    assert(all(out[i] <= out[i + 1] for i in range(n - 1)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
