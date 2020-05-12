---
title: python script vose vose alias test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vose vose alias test'

Functions in program: 
* `def test_c(count):`
* `def test_b(number_of_labels, count):`
* `def test_a(count):`
* `def _do_test(vose, dist, count):`

Modules used in program: 
* `import functools`
* `import random`
* `import vose_alias`

## python vose vose alias test

Python example: vose vose alias test

```python
import vose_alias
import random
import functools


def _do_test(vose, dist, count):

    counters = {}
    for d in dist:
        counters[d[0]] = 0

    for _ in range(count):
        counters[vose()] += 1/count

    return counters


def test_a(count):

    dist = [ ('a', 25), ('b',65 ), ('c', 10)]

    vose = vose_alias.VoseAlias(dist)

    counters = _do_test(vose, dist, count)
    sum_weight = functools.reduce(lambda x, y: x + y[1], dist, 0.0)


    for d in dist:
        delta = 100*(d[1]/sum_weight) - (100 * counters[d[0]])
        print(f"{d[0]}:{100*(d[1]/sum_weight)} => {100*counters[d[0]]} delta:{delta}")



def test_b(number_of_labels, count):

    dist = []
    for i in range(number_of_labels):
        label = f"a{i}"
        dist.append((label, random.randint(1,100)))

    vose = vose_alias.VoseAlias(dist)

    counters = _do_test(vose, dist, count)

    sum_weight = functools.reduce(lambda x, y: x + y[1], dist, 0.0)

    for d in dist:
        delta = 100*(d[1]/sum_weight) - (100 * counters[d[0]])
        print(f"{d[0]}:{100*(d[1]/sum_weight)} => {100*counters[d[0]]} delta:{delta}")

def test_c(count):

    dist = [('1', 1), ('2', 1), ('3', 1), ('4', 1), ('5', 1), ('6', 1)]

    vose = vose_alias.VoseAlias(dist)

    counters = _do_test(vose, dist, count)
    sum_weight = functools.reduce(lambda x, y: x + y[1], dist, 0.0)

    for d in dist:
        delta = 100 * (d[1] / sum_weight) - (100 * counters[d[0]])
        print(f"{d[0]}:{100*(d[1]/sum_weight):0.3f} => {100*counters[d[0]]:05.02f} delta:{delta:+0.3f}")



#test_a(1000)

#test_b(1000, 1000000)

test_c(1000000)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
