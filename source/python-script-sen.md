---
title: python script sen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sen'

Functions in program: 
* `def random_multisplitter(word):`
* `def random_int(s):`

Modules used in program: 
* `import random`

## python sen

Python example: sen

```python
import random

def random_int(s):
  return random.randint(1,len(s))

def random_multisplitter(word):
    from numpy import mod
    spw = []
    length = len(word)
    rand = random_int(word)
    if rand == length:       #probability of not splitting
        return [word]

    else:
        div = mod(rand, (length + 1))  #defining division points 
        bound = length - div
        spw.append(div)
        while div != 0:
            rand = random_int(word)
            div = mod(rand,(bound+1))
            bound = bound-div
            spw.append(div)
        result = spw
    b = 0
    points =[]
    for x in range(len(result)-1): #calculating splitting points 
        b=b+result[x]
        points.append(b)
    xy=0
    t=[]
    for i in points:
        t.append(word[xy:i])
        xy=i
    if word[xy:len(word)]!='':
        t.append(word[xy:len(word)])
    if type(t)!=list:
        return [t]
    return t



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
