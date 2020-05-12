---
title: python script object (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'object'


## python object

Python example: object

```python
# -*- coding: utf-8 -*-

# 对象
class Complex:
    def __init__(self, real_part, imaginary_part):
        self.r = real_part
        self.i = imaginary_part


if __name__ == '__main__':
    c = Complex(3, 4)
    print("{} + {}i".format(c.r, c.i))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
