---
title: python script shuffle cards (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'shuffle cards'

Functions in program: 
* `def shuffle(cards):`

Modules used in program: 
* `import random`

## python shuffle cards

Python example: shuffle cards

```python
import random

cards =  ["card_{}".format(i) for i in range(1, 55)]

def shuffle(cards):
    random.shuffle(cards)
    return cards

print(cards)
print(shuffle(cards))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
