---
title: python script sorts test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sorts test'

Functions in program: 
* `def test(sort_m, color_i):`

Modules used in program: 
* `import gc`
* `import random`
* `import sorts_nlogn`
* `import sorts_n2`

## python sorts test

Python example: sorts test

```python
from timeit import default_timer as timer
from matplotlib import pyplot as plt
import sorts_n2
import sorts_nlogn
import random
import gc

colors = ('b', 'g', 'r', 'c', 'm', 'y', 'k', 'w')
color_i = 0

def test(sort_m, color_i):
    results = [0] * 1001
    for _ in range(50):
        for i in range(1001):
            sorted_list = [random.randint(0, 9) for n in range(i)]
            #chk = sorted(sorted_list)
            start = timer()
            sort_m(sorted_list)
            stop = timer()
            #if sorted_list != chk:
            #    raise ValueError(sort_m.__name__ + ' bad sort with '
            #                     + str(i-1) + 'elements')
            results[i] += stop - start
    for i in range(1001):
        results[i] /= 50
    plt.plot(results, colors[color_i], alpha=0.5, label=sort_m.__name__)

sorted_methods = [
    sorts_n2.selection_sort,
    sorts_n2.bubble_sort,
    sorts_n2.shaker_sort,
    sorts_n2.gnome_sort,
    sorts_nlogn.merge_sort
                ]
gc.disable()
for sorted_method in sorted_methods:
    test(sorted_method, color_i)
    color_i += 1
    gc.collect()
plt.title('Sorts')
plt.legend(loc='upper left')
plt.xlabel('n')
plt.ylabel('sort time')
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
