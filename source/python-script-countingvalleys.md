---
title: python script countingvalleys (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'countingvalleys'

Functions in program: 
* `def countingValleys(n, s):`

Modules used in program: 
* `import sys`
* `import re`
* `import random`
* `import os`
* `import math`

## python countingvalleys

Python example: countingvalleys

```python
#!/bin/python3

import math
import os
import random
import re
import sys

# Complete the countingValleys function below.
def countingValleys(n, s):
    valley=0
    land=0
    for i in s:

        if i=='U':

            valley+=1

        if i=='D':

            valley+=-1

        if valley==0 and i=='U':

            valley+=1
    return valley
    

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input())

    s = input()

    result = countingValleys(n, s)

    fptr.write(str(result) + '\n')

    fptr.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
