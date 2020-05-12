---
title: python script dictionary (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dictionary'

Functions in program: 
* `def twoStrings(s1, s2):`
* `def checkMagazine(magazine, note):`

Modules used in program: 
* `import sys`
* `import re`
* `import random`
* `import os`
* `import math`

## python dictionary

Python example: dictionary

```python
# https://www.hackerrank.com/challenges/ctci-ransom-note/problem

#!/bin/python3

import math
import os
import random
import re
import sys

# Complete the checkMagazine function below.
def checkMagazine(magazine, note):
    magazine_dict = {}
    for word in magazine:
        value = magazine_dict.get(word, 0) + 1
        magazine_dict.update({word: value})

    for noteWord in note:
        if magazine_dict.get(noteWord, 0) > 0:
            magazine_dict.update({noteWord: magazine_dict.get(noteWord) - 1})
        else:
            print("No")
            return

    print('Yes')

# https://www.hackerrank.com/challenges/two-strings/problem
# Complete the twoStrings function below.
# hello / world = YES
# hi / world = NO
def twoStrings(s1, s2):
    for char in list(s1):
        if char in s2:
            return 'YES'
    return 'NO'


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
