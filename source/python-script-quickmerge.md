---
title: python script quickmerge (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quickmerge'

Functions in program: 
* `def mergesort(list):`
* `def quicksort(list):`

## python quickmerge

Python example: quickmerge

```python
def quicksort(list):
    #print("quick>", list)
    if len(list) <= 1:
        return list

    pivot = list[len(list)//2]
    a = mergesort([x for x in list if x <= pivot])
    b = mergesort([x for x in list if not x <= pivot])
    #print("quick<", a+b)
    return a + b

def mergesort(list):
    #print("merge>", list)
    if len(list) <= 1:
        return list

    mid = len(list)//2
    a = quicksort(list[:mid])[::-1]
    b = quicksort(list[mid:])[::-1]
    merge = []
    while a and b:
        if a[-1] <= b[-1]:
            merge.append(a.pop())
        else:
            merge.append(b.pop())
    merge.extend(a[::-1])
    merge.extend(b[::-1])
    #print("merge<", merge)
    return merge

if __name__ == '__main__':
    import random
    random.seed(1)
    print(quicksort(random.sample(xrange(10), 10)))
    print(mergesort(random.sample(xrange(10), 10)))

    import timeit
    for alg in "quicksort", "mergesort":
        for n in 10, 100, 1000, 10000:
            setup = "from __main__ import {1}; import random; l = random.sample(xrange({0}), {0})".format(n, alg)
            t = timeit.timeit(alg+"(l)", setup, number=100000/n) / float(100000/n)
            print("{0} {1:-5d}: {2:f} seconds".format(alg, n, t))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
