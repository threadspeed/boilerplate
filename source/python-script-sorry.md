---
title: python script sorry (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sorry'


Modules used in program: 
* `import random`
* `import itertools as it`
* `import sys`

## python sorry

Python mysql example: sorry

```python
import sys
import itertools as it
import random

cards = [1] + 5 * [1, 2, 3, 4, 5, 7, 8, 10, 11, 12, 'Sorry!']
shuffled = lambda x: random.sample(x, len(x))

deck = it.chain.from_iterable((shuffled(cards) for _ in it.count()))

for l in sys.stdin:
    print(next(deck))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
