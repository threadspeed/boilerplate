---
title: python script nom 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nom 2'

Functions in program: 
* `def main():`
* `def normal_distribution(x, sigma, mu):`
* `def transformation_box_muller(a1, a2):`

## python nom 2

Python mysql example: nom 2

```python
# -*- coding: utf-8 -*-


from random import random
from math import *


def transformation_box_muller(a1, a2):
    return sqrt(2*log(1/a1))*sin(2*pi*a2)


def normal_distribution(x, sigma, mu):
    return (1/(sigma*sqrt(2*pi)))*exp(-(x-mu)**2/(2*sigma**2))


def main():
    a1 = random()
    a2 = random()
    x = transformation_box_muller(a1, a2)
    print(normal_distribution(x, 1, 0))


if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
