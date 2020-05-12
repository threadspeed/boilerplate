---
title: python script norm-distribute (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'norm-distribute'


Modules used in program: 
* `import concurrent.futures`
* `import sys`
* `import numpy as np`
* `import random`

## python norm-distribute

Python mysql example: norm-distribute

```python
from scipy import stats

import random

from collections import Counter

import numpy as np

import sys

import concurrent.futures
# 多重混合分布
if '--mix' in sys.argv:

  def _map(arg):
    head_freq = {}
    for i in range(1000000):
      #scale = np.abs( np.random.normal(loc=0.0, scale=random.random(), size=1) ) * 10000
      #scale = scale.tolist().pop(0)
      #loc = np.abs( np.random.normal(loc=0.0, scale=random.random(), size=1) ) * 10000
      #loc = loc.tolist().pop(0)
      loc, scale = [random.randint(0, 10e10) for i in range(2)]
      sample = np.abs( np.random.normal(loc=loc, scale=scale, size=1) )
      sample = sample.tolist().pop(0)
      sample = int(sample)
      head = (list(f'{sample}').pop(0))
      if head_freq.get(head) is None:
        head_freq[head] = 0
      head_freq[head] += 1

    return head_freq

  head_freq = {}
  with concurrent.futures.ProcessPoolExecutor(max_workers=16) as exe:
    for _head_freq in exe.map(_map, list(range(16))):
      for head, freq in _head_freq.items():
        if head_freq.get(head) is None:
          head_freq[head] = 0
        head_freq[head] += freq
total = sum(head_freq.values())
for head, freq in sorted(head_freq.items(), key=lambda x:x[1]*-1):
  print(head, freq, freq/total)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
