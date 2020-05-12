---
title: python script Pre-class%25206.2 Randomized Quicksort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Pre-class%25206.2 Randomized Quicksort'

Functions in program: 
* `def quick_sort_recursive_checker():`
* `def test_quicksort():`
* `def randomized_quicksort():`
* `def qsort(lst):`
* `def median(x1, x2, x3):`
* `def test_quicksort():`
* `def randomized_quicksort():`
* `def qsort(lst):`
* `def median(x1, x2, x3):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import timeit`
* `import random`
* `import timeit`

## python Pre-class%25206.2 Randomized Quicksort

Python example: Pre-class%25206.2 Randomized Quicksort

```python
#Without separating items that are equal to the parition

import timeit
import random

eps = 1e-16
N = 100
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
        if frm == to:
            continue

        # Find the partition:
        N = to - frm #Length of subarray
        inds = [frm + int(N * n) for n in locations] #Assigning indices
        values = [lst[ind] for ind in inds] #Values of indices
        partition = median(*values) #Median of values

        # Split into lists:
        lower = [a for a in lst[frm:to] if a <= partition]
        upper = [a for a in lst[frm:to] if a > partition]

        ind1 = frm + len(lower)

        # Push back into correct place:
        lst[frm:ind1] = lower
        lst[ind1:to] = upper

        # Enqueue other locations
        indices.append((frm, ind1))
        indices.append((ind1, to))
    return lst


def randomized_quicksort():
    lst = [i for i in range(N)]
    random.shuffle(lst)
    return qsort(lst)


def test_quicksort():
    lst = randomized_quicksort()
    assert (lst == [i for i in range(N)])


# Is our algorithm correct
print(test_quicksort())



# Q.1.
'''
In the case where our array consists only of duplicates, shuffling the list has no effect.
Thus, removing the separation of items equal to the partition, this algorithm behaves like the implementation from 5.2
As every number is equal to the partition, the partition will always end up at one end of the array.
Splitting it into two subarrays of length 0 and n-1. This means the runtime is O(n^2)
'''

#Q.2.
'''
Prior to modifications, count == array.length.
Thus, the subarrays would be of length 0 and 0, terminating the recursion immediately.
This means the dominant cost is incurred by the median finding procedure, which I am unsure the complexity of.
The reason I am unsure is that it uses code I have never seen before:
the ufunction is built to take three arguments as input. 
I understand that the asterisk (*) is somehow unpacking the values list, somehow.
My guess is that it is somehow making recursive calls to median. However I am not sure how this works.
Complexity: Theta(m), there m is the complexity of the median finding procedure.
'''





#Without median partition

import timeit
import random

eps = 1e-16
N = 100
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
        if frm == to:
            continue

        # Find the partition:
        partition = lst[frm]

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
    return lst


def randomized_quicksort():
    lst = [i for i in range(N)]
    random.shuffle(lst)
    return qsort(lst)


def test_quicksort():
    lst = randomized_quicksort()
    assert (lst == [i for i in range(N)])


# Is our algorithm correct
print(test_quicksort())

# How fast is our algorithm


#Q1
'''
What the median selection does, is that it enforces balanced partitioning.
If we remove it and instead select the first element, then we have no guarantee that partitions will be balanced.
However, this implementation shuffles the list before we call quicksort. 
Thus, the list will be random in expectation, which means expected run time O(n log n).
'''

#Q2
'''
Yes, it will change practical run time, even though it will have the same average case time complexity.
The benefit of the median-partition is that it enforces even partitions -> Worst case O(n log n).
However, there is a cost associated with finding the median. 
This cost is incurred for every recursive call to quicksort.
Whilst this does not affect the asymptotic run time, it affects the pracitcal runtime.
If my suspicion is correct, that the median finding is itself recursive, that means we have separate recurssive functions inside recursive functions.
The overhead could be quite large and we may even see lower practical run times without median partition.
'''


#Check if merge_sort_3 works by comparing to built-in sort function
import numpy as np


ns = [10**n for n in range(10)]
print(ns)
def quick_sort_recursive_checker():
    j = 0
    correct = True
    for n in ns:
    #Check up to 50 times
        while j <= 50 and correct:
        
            #On random list of length between 0 and 1000, 
            #with values between -100 and 100
            test_array = list(np.random.randint(
                -100, 100, n))
        
            #Sort using built-in function
            a = test_array
            a.sort()
        
            #If sorted arrays don't match, return False
            if a != quick_sort_recursive(test_array):
                correct = False
        
            #increment j
            j += 1
        
    return correct

quick_sort_recursive_checker()


#How low can you go? Limbo
'''
If by "can only make 500 recursive calls," it is meant that teh recursion tree can only be 500 levels deep, then
in the worst case where completely uneven partitions are formed, we have the recurrence relationship:
T(n) = T(n-1)
This means a tree will have n levels --> IN the worst case we can sort an array fo length 500.
In the best case, where two balanced partitions are formed every iteration, we have the recurrence relationship:
T(n) = 2T(n/2)
A tree, then, will have log_2(n) levels. log_2(n) = 500, solve for n --> 3273390607896141870013189696827599152216642046043064789483291368096133\
796404674554883270092325904157150886684127560071009217256545885393053328527589376. = 2^500.
I.e. In the best case, you can sort seriously large lists.
'''

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
