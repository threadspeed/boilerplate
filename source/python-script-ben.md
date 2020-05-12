---
title: python script ben (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ben'

Functions in program: 
* `def rms(s):`

Modules used in program: 
* `import math, random`

## python ben

Python example: ben

```python
import math, random

def rms(s):
  num_splits = float(random.randint(1, len(s)))
  #print('nums', num_splits)

  chars_left = len(s)
  for _ in range(int(num_splits - 1)):
    min_chars_in_chunk = 1
    #print('\t', 'minc', min_chars_in_chunk)

    max_chars_in_chunk = int(math.ceil(chars_left / num_splits))
    #print('\t', 'maxc', max_chars_in_chunk)

    num_chars = random.randint(min_chars_in_chunk, max_chars_in_chunk)    
    #print('\t', 'numc', num_chars)

    yieldval = s[-chars_left:num_chars-chars_left]
    #print('\t', 'chun', yieldval)

    yield yieldval

    chars_left-=num_chars
    #print

  yield s[-chars_left:]


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
