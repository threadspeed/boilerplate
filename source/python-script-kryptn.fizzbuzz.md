---
title: python script kryptn.fizzbuzz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'kryptn.fizzbuzz'

Functions in program: 
* `def fizzbuzz():`

## python kryptn.fizzbuzz

Python mysql example: kryptn.fizzbuzz

```python
def fizzbuzz():
    import random

    def magic(number=24866068):
        while True:
            random.seed(number)
            for x in range(15):
                n = int(random.random() * 10000) % 4
                yield 'fizzbuzz'[(n*4-4)%8:n*4]

    for i, m in zip(range(1, 101), magic()):
        print(m or i)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
