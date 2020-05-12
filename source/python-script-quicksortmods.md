---
title: python script quicksortmods (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quicksortmods'

Functions in program: 
* `def test_quicksort():`
* `def randomized_quicksort():`
* `def qsort(lst, frm, to):`
* `def median(x1, x2, x3):`
* `def test_quicksort():`
* `def randomized_quicksort():`
* `def qsort(lst):`
* `def test_quicksort():`
* `def randomized_quicksort():`
* `def qsort(lst):`
* `def median(x1, x2, x3):`

Modules used in program: 
* `import random`
* `import timeit`
* `import random`
* `import timeit`
* `import random`
* `import timeit`

## python quicksortmods

Python example: quicksortmods

```python

# coding: utf-8

# In[10]:


##quicksort without separating equal items

import timeit
import random

eps = 1e-16
N = 2
locations = [0.0, 0.5, 1.0 - eps]


def median(x1, x2, x3):
    if (x1 < x2 < x3) or (x3 < x2 < x1):
        return x2
    elif (x1 < x3 < x2) or (x2 < x3 < x1):
        return x3
    else:
        return x1

def qsort(lst):
    indices = [(0, len(lst))]

    while indices:
        (frm, to) = indices.pop()
        if frm >= to:
            print(frm, to)
            print(indices)
            continue

        # Find the partition:
        N = to - frm
        inds = [frm + int(N * n) for n in locations]
        values = [lst[ind] for ind in inds]
        partition = median(*values)

        # Split into lists:
        lower = [a for a in lst[frm:to] if a <= partition]
        upper = [a for a in lst[frm:to] if a > partition]
        #counts = sum([1 for a in lst[frm:to] if a == partition])

        ind1 = frm + len(lower) 
        ind2 = to - len(upper)

        # Push back into correct place:
        lst[frm:ind1] = lower
        #lst[ind1:ind2] = [partition] * counts
        lst[ind2:to] = upper

        # Enqueue other locations
        if frm < ind1:
            indices.append((frm, ind1))
        if ind2 < to:
            indices.append((ind2, to))
        print(indices)
    return lst


def randomized_quicksort():
    lst = [i for i in range(N)]
    random.shuffle(lst)
    return qsort(lst)


def test_quicksort():
    lst = randomized_quicksort()
    assert (lst == [i for i in range(N)])


# Is our algorithm correct
test_quicksort()

# How fast is our algorithm
print(timeit.timeit(randomized_quicksort, number=1))


# In[13]:


##quicksort using first element as partition

import timeit
import random

eps = 1e-16
N = 10000
locations = [0.0, 0.5, 1.0 - eps]



def qsort(lst):
    indices = [(0, len(lst))]

    while indices:
        (frm, to) = indices.pop()
        if frm == to:
            continue

        # Find the partition:
        partition = lst[0]

        # Split into lists:
        lower = [a for a in lst[frm:to] if a < partition]
        upper = [a for a in lst[frm:to] if a > partition]
        counts = sum([1 for a in lst[frm:to] if a == partition])

        ind1 = frm + len(lower)
        ind2 = ind1 + counts

        # Push back into correct place:
        lst[frm:ind1] = lower
        lst[ind1:ind2] = [partition] * counts
        lst[ind2:to] = upper

        # Enqueue other locations
        indices.append((frm, ind1))
        indices.append((ind2, to))
        print(indices)
    return lst


def randomized_quicksort():
    lst = [i for i in range(N)]
    random.shuffle(lst)
    return qsort(lst)


def test_quicksort():
    lst = randomized_quicksort()
    assert (lst == [i for i in range(N)])


# Is our algorithm correct
test_quicksort()

# How fast is our algorithm
print(timeit.timeit(randomized_quicksort, number=1))


# In[17]:


##recursive quicksort

import timeit
import random

eps = 1e-16
N = 10000
locations = [0.0, 0.5, 1.0 - eps]


def median(x1, x2, x3):
    if (x1 < x2 < x3) or (x3 < x2 < x1):
        return x2
    elif (x1 < x3 < x2) or (x2 < x3 < x1):
        return x3
    else:
        return x1

def qsort(lst, frm, to):

    if frm < to:    
        # Find the partition:
        N = to - frm
        inds = [frm + int(N * n) for n in locations]
        values = [lst[ind] for ind in inds]
        partition = median(*values)

        # Split into lists:
        lower = [a for a in lst[frm:to] if a < partition]
        upper = [a for a in lst[frm:to] if a > partition]
        counts = sum([1 for a in lst[frm:to] if a == partition])

        ind1 = frm + len(lower)
        ind2 = ind1 + counts

        # Push back into correct place:
        lst[frm:ind1] = lower
        lst[ind1:ind2] = [partition] * counts
        lst[ind2:to] = upper

        # recursively call function on partitioned lists
        qsort(lst[frm:ind1], frm, ind1)
        qsort(lst[ind2:to], ind2, to)
    return lst


def randomized_quicksort():
    lst = [i for i in range(N)]
    random.shuffle(lst)
    return qsort(lst, 0, len(lst) - 1)


def test_quicksort():
    lst = randomized_quicksort()
    assert (lst == [i for i in range(N)])


# Is our algorithm correct
test_quicksort()

# How fast is our algorithm
print(timeit.timeit(randomized_quicksort, number=1))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
