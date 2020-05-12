---
title: python script predict binary (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'predict binary'

Functions in program: 
* `def mode_slice(lst, n):`
* `def binary_mode(lst):`
* `def binary_str(length):`
* `def binary_lst(length):`

## python predict binary

Python mysql example: predict binary

```python
#make random 1's and 0's

def binary_lst(length):
    import random
    return [random.randrange(0,2) for elem in range(length)]
  #string of random 1's and 0's  
def binary_str(length):
    import random
    return ''.join([str(random.randrange(0,2)) for elem in range(length)])
#gets more common element in list    
def binary_mode(lst):
    count = {lst.count(elem):elem for elem in [0, 1]}
    return count[max(count.keys())]

#gets most common element in list increment
#   f[::2]
#=> [1, 3, 5, 7]
def mode_slice(lst, n):
    return binary_mode(lst[::n])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
