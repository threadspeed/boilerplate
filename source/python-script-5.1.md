---
title: python script 5.1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5.1'

Functions in program: 
* `def shuffle(a): `
* `def sort_test(a): `
* `def badalgo(a): `

Modules used in program: 
* `import random `

## python 5.1

Python mysql example: 5.1

```python
import random 
  
def badalgo(a): 
    n = len(a) 
    while (sort_test(a)== False): 
        shuffle(a) 
# To check if array is sorted or not 
def sort_test(a): 
    n = len(a) 
    for i in range(0, n-1): 
        if (a[i] > a[i+1] ): 
            return False
    return True

# To generate permuatation of the array 
def shuffle(a): 
    n = len(a) 
    for i in range (0,n): 
        r = random.randint(0,n-1) 
        a[i], a[r] = a[r], a[i] 

# Driver code to test above 
a = [3, 2, 4, 1, 0, 5] 
badalgo(a) 
print("Sorted array is :") 
for i in range(len(a)): 
    print(("%d" %a[i]), )

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
