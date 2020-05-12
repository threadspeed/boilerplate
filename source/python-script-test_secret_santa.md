---
title: python script test secret santa (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test secret santa'

Functions in program: 
* `def test_returns_same_result(capsys):`

## python test secret santa

Python example: test secret santa

```python
# -*- coding: utf-8 -*-
from secret_santa import main


def test_returns_same_result(capsys):
    main(1, 'info')
    stdout, _ = capsys.readouterr()

    assert stdout == u"""x dāvina dāvanu b
b dāvina dāvanu z
z dāvina dāvanu a
a dāvina dāvanu y
y dāvina dāvanu c
c dāvina dāvanu x
"""


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
