---
title: python script mergebench (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mergebench'

Functions in program: 
* `def bubble_sort (l):`
* `def tcomergesort(l):`
* `def leftcomb(l):`
* `def tcomergeSort(array):`
* `def tco_cpsmergeSort(array,continuation):`
* `def trampoline(bouncer):`
* `def cpsmergeSort(array,continuation):`
* `def cps_merge_sort(array):`
* `def fastmergeSort(array):`
* `def fastmerge(array1,array2):`
* `def nolenmergeSort(array):`
* `def nolenmerge(array1,array2):`
* `def badmerge(array1,array2):`
* `def badmergeSort(array):`

Modules used in program: 
* `import timeit`

## python mergebench

Python example: mergebench

```python
import timeit

def badmergeSort(array):
    if len(array) <= 1:
        return array
    else:
        left = array[:len(array)/2]
        right = array[len(array)/2:]
        return badmerge(badmergeSort(left),badmergeSort(right))

def badmerge(array1,array2):
    merged_array=[]
    while len(array1) > 0 or len(array2) > 0:

        if array2 and not array1:
            merged_array.append(array2.pop(0))

        elif (array1 and not array2) or array1[0] < array2[0]:
            merged_array.append(array1.pop(0))

        else:
            merged_array.append(array2.pop(0))
    return merged_array

def nolenmerge(array1,array2):
    merged_array=[]
    while array1 or array2:
        if not array1:
            merged_array.append(array2.pop(0))
        elif (not array2) or array1[0] < array2[0]:
            merged_array.append(array1.pop(0))
        else:
            merged_array.append(array2.pop(0))
    return merged_array

def nolenmergeSort(array):
    n  = len(array)
    if n <= 1:
        return array
    left = array[:n/2]
    right = array[n/2:]
    return nolenmerge(nolenmergeSort(left),nolenmergeSort(right))

assert nolenmergeSort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

def fastmerge(array1,array2):
    merged_array=[]
    while array1 or array2:
        if not array1:
            merged_array.append(array2.pop())
        elif (not array2) or array1[-1] > array2[-1]:
            merged_array.append(array1.pop())
        else:
            merged_array.append(array2.pop())
    merged_array.reverse()
    return merged_array

def fastmergeSort(array):
    n  = len(array)
    if n <= 1:
        return array
    left = array[:n/2]
    right = array[n/2:]
    return fastmerge(fastmergeSort(left),fastmergeSort(right))

assert fastmergeSort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Alone, this will run out of recursion depth because Python does not do TCO,
# for lists of length > 100

def cps_merge_sort(array):
    return cpsmergeSort(array,lambda x:x)

def cpsmergeSort(array,continuation):
    n  = len(array)
    if n <= 1:
        return continuation(array)
    left = array[:n/2]
    right = array[n/2:]
    return cpsmergeSort (left, lambda leftR:
                         cpsmergeSort(right, lambda rightR:
                                      continuation(fastmerge(leftR,rightR))))

assert cps_merge_sort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

# This is trampoline-based tco elimination (not very efficient)

thunk = lambda name, *args: lambda: name(*args)

def trampoline(bouncer):
    while callable(bouncer):
        bouncer = bouncer()
    return bouncer

def tco_cpsmergeSort(array,continuation):
    n  = len(array)
    if n <= 1:
        return continuation(array)
    left = array[:n/2]
    right = array[n/2:]
    return thunk (tco_cpsmergeSort, left, lambda leftR:
                  thunk (tco_cpsmergeSort, right, lambda rightR:
                         (continuation(fastmerge(leftR,rightR)))))

mycpomergesort = lambda l: trampoline(tco_cpsmergeSort(l,lambda x:x))

assert mycpomergesort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

# That's not a problem ! We can do TCO ourselves !

def tcomergeSort(array):
    sortedstuff,tosort = [],[array]
    while tosort:
        array = tosort.pop()
        n = len(array)
        if n > 1: # this is a normal call, recurse
            tosort.append(array[n/2:])
            tosort.append(array[:n/2])
        else:# we're returning : integrate the nodes to the sorted stuff
            while sortedstuff:
                leftR = sortedstuff.pop()
                array = fastmerge(leftR,array)
            sortedstuff.append(array)
    return sortedstuff[0]

assert tcomergeSort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

def leftcomb(l):
    maxn,leftcomb = len(l),[]
    n = maxn/2
    while maxn > 1:
        leftcomb.append((l[n:maxn],False))
        maxn,n = n,n/2
    return l[:maxn],leftcomb

def tcomergesort(l):
    l,stack = leftcomb(l)
    while stack: # l sorted, stack contains tagged slices
        i,ordered = stack.pop()
        if ordered:
            l = fastmerge(l,i)
        else:
            stack.append((l,True)) # store return call
            rsub,ssub = leftcomb(i)
            stack.extend(ssub) #recurse
            l = rsub
    return l

assert tcomergesort([9,8,7,6,5,4,3,2,1]) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

def bubble_sort (l):
    swapped = True
    while swapped:
        swapped = False
        for i in xrange(len(l)-1):
            if l[i] > l[i+1]:
                l[i],l[i+1] = l[i+1],l[i]
                swapped = True

# Python's native timsort
code = 'import random; l = random.sample(xrange(10000000), 10000); l.sort()'
t = timeit.Timer(code)
print("Python's native (Tim)sort time:",t.timeit(100) / 100)
# The slow bubble sort (don't have the patience to test on more than 1)
code = 'import random; l = random.sample(xrange(10000000), 10000); bubble_sort(l)'
t = timeit.Timer(code,'from __main__ import bubble_sort')
print("Bubblesort time:",t.timeit(1) / 1)
# badmerge sort
code = 'import random; l = random.sample(xrange(10000000), 10000); badmergeSort(l)'
t = timeit.Timer(code,'from __main__ import badmergeSort')
print("Original Mergesort  time:",t.timeit(100) / 100)
# merge sort
code = 'import random; l = random.sample(xrange(10000000), 10000); nolenmergeSort(l)'
t = timeit.Timer(code,'from __main__ import nolenmergeSort')
print("no-len Mergesort  time:",t.timeit(100) / 100)
# fast merge sort
code = 'import random; l = random.sample(xrange(10000000), 10000); fastmergeSort(l)'
t = timeit.Timer(code,'from __main__ import fastmergeSort')
print("no-len Mergesort + fastmerge time:",t.timeit(100) / 100)
# trampolined tail-recursive fast merge sort
code = 'import random; l = random.sample(xrange(10000000), 10000); mycpomergesort(l)'
t = timeit.Timer(code,'from __main__ import mycpomergesort')
print("trampolined mergesort + fastmerge time:",t.timeit(100) / 100)
# manually tail-call-eliminated fast merge sort
code = 'import random; l = random.sample(xrange(10000000), 10000); tcomergesort(l)'
t = timeit.Timer(code,'from __main__ import tcomergesort')
print("Manual tail-call-optimized mergesort + fastmerge time:",t.timeit(100) / 100)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
