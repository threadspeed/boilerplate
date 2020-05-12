---
title: python script diffieTest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'diffieTest'

Functions in program: 
* `def external():`
* `def internal():`

Modules used in program: 
* `import random`
* `import diffieHellman as dif`

## python diffieTest

Python mysql example: diffieTest

```python
import diffieHellman as dif
import random

def internal():
    p = dif.randomPrime(1000,5000)
    g = random.randint(100000,500000)
    print('p,g done')
    aPr = random.randint(100000,500000)
    bPr = random.randint(100000,500000)
    print('pr done')
    aPu = dif.genPub(aPr,g,p)
    bPu = dif.genPub(bPr,g,p)
    print('pu done')
    aKey = dif.genKey(bPu,aPr,p)
    bKey = dif.genKey(aPu,bPr,p)
    print('key done')

    print('\nnp:',p,'\ng:',g,'\naPr:',aPr,'\nbPr:',bPr,'\naPu:',aPu,'\nbPu:',bPu,'\naKey:',aKey,'\nbKey:',bKey)

def external():
    g = 3
    p = 7
    aPr = 7 #random.randint(100000,500000)
    print(aPr)
    aPu = dif.genPub(aPr,g,p)
    print(aPu)
    key = dif.genKey(aPu,int(input()),p)
    print(key)

internal()
external()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
