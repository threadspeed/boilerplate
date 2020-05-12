---
title: python script sherlock and anagrams (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sherlock and anagrams'

Functions in program: 
* `def sherlockAndAnagrams(s):`

Modules used in program: 
* `import sys`
* `import re`
* `import random`
* `import os`
* `import math`

## python sherlock and anagrams

Python example: sherlock and anagrams

```python
#
# https://www.hackerrank.com/challenges/sherlock-and-anagrams/problem
#
#!/bin/python3

import math
import os
import random
import re
import sys

# Complete the sherlockAndAnagrams function below.
def sherlockAndAnagrams(s):
    count = 0
    for i in range(1, len(s)):
        splited_list = []
        for x in range(0, len(s)):
            offset = x + i
            if offset > len(s):
                continue
            x = ''.join(sorted(s[x:offset]))
            
            for z in splited_list:
                if z == x:
                    count += 1
                    
            splited_list.append(x)
        print(splited_list)
    print(count)
    return count

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
