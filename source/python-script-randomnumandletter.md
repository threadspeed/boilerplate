---
title: python script randomnumandletter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randomnumandletter'

Functions in program: 
* `def randletter():`
* `def randnum(maxn):`

## python randomnumandletter

Python mysql example: randomnumandletter

```python
#random generator

#yields random number
def randnum(maxn):
    import random
    while True:
        yield random.randrange(maxn)
        
        
        
#yields random letter
def randletter():
    import random
    letters = list("abcdefghijklmnopqrstuvwxyz")
    while True:
        yield random.choice(letters)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
