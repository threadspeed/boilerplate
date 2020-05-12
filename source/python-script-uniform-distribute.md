---
title: python script uniform-distribute (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'uniform-distribute'

Functions in program: 
* `def _map(arg):`

Modules used in program: 
* `import math`
* `import concurrent.futures`
* `import sys`
* `import numpy as np`
* `import random`

## python uniform-distribute

Python example: uniform-distribute

```python
from scipy import stats

import random

from collections import Counter

import numpy as np

import sys

import concurrent.futures

import math
def _map(arg):
  head_freq = {}
  uniforms = np.random.randint(0, 10e7, size=100000)
  for uniform in uniforms.tolist():
    #uniform = math.log(uniform)
    head = (list(f'{uniform}').pop(0))
    if head_freq.get(head) is None:
      head_freq[head] = 0
    head_freq[head] += 1

  return head_freq

head_freq = {}
#_map(1)
with concurrent.futures.ProcessPoolExecutor(max_workers=16) as exe:
  for _head_freq in exe.map(_map, list(range(16))):
    for head, freq in _head_freq.items():
      if head_freq.get(head) is None:
        head_freq[head] = 0
      head_freq[head] += freq


total = sum(head_freq.values())
for head, freq in sorted(head_freq.items(), key=lambda x:x[0]):
  print(head, freq, freq/total)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
