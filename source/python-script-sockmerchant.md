---
title: python script sockmerchant (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sockmerchant'

Functions in program: 
* `def sockMerchant(n, ar):`

Modules used in program: 
* `import sys`
* `import re`
* `import random`
* `import os`
* `import math`

## python sockmerchant

Python example: sockmerchant

```python
#!/bin/python3

import math
import os
import random
import re
import sys
from collections import Counter

# Complete the sockMerchant function below.
def sockMerchant(n, ar):
    # solution uses v as value toensure quotient returned is 0, checks value count through .items
    return sum( v//2 for k,v in Counter(ar).items())
if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input())

    ar = list(map(int, input().rstrip().split()))

    result = sockMerchant(n, ar)

    fptr.write(str(result) + '\n')

    fptr.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
