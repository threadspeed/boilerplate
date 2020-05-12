---
title: python script GiftExchangePairGenerator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GiftExchangePairGenerator'

Functions in program: 
* `def good_pair(ignore_ppl, chosen1, chosen2):`
* `def getRandomPerson(ppl):`

Modules used in program: 
* `import random`

## python GiftExchangePairGenerator

Python example: GiftExchangePairGenerator

```python
# -*- coding: utf-8 -*-
import random


def getRandomPerson(ppl):
    return ppl[random.randint(0,len(ppl)-1)]


def good_pair(ignore_ppl, chosen1, chosen2):
    for pair in ignore_ppl:
        if chosen1 in pair and chosen2 in pair:
            return False
    return True


ppl = ['x', 'y', 'z', 'a', 'b', 'c']
ignore_ppl = [['x', 'y'],['x', 'c']]

#Ja lasa failu no stdin
#ppl = [line.strip() for line in open(str(sys.argv[1]))]
#ignore_ppl = [line.split() for line in open(str(sys.argv[2]))]

result = []

while len(ppl) > 0:
    chosen = getRandomPerson(ppl)
    while result and not good_pair(ignore_ppl, chosen, result[len(result) - 1]):
        chosen = getRandomPerson(ppl)
    result.append(chosen)
    ppl.remove(chosen)

for i in range(0, len(result)):
   if i is len(result) - 1:
       print(result[i] + " dāvina dāvanu " + result[0])
   else:
       print(result[i] + " dāvina dāvanu " + result[i+1])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
