---
title: python script remove common (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'remove common'

Functions in program: 
* `def remove_common_v2(le): #removing common elements by using set `
* `def remove_common_v1(le): #removing common elements from a random list`

## python remove common

Python mysql example: remove common

```python
# creating a  random list and removing duplicate elements

def remove_common_v1(le): #removing common elements from a random list
    import random
    l=[]
    for i in range(le):
            l.append(random.randint(1,10))
    print("Here is the list",list(dict.fromkeys(l)))
remove_common_v1(int(input("enter the length ")))

def remove_common_v2(le): #removing common elements by using set 
    import random
    l=[]
    for i in range(le):
        l.append(random.randint(1,10))
    print("Here is the list by using sets ",list(set(l)))
remove_common_v2(int(input("Enter the length ")))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
