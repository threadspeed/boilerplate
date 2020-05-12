---
title: python script 5 pi estimate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5 pi estimate'


## python 5 pi estimate

Python example: 5 pi estimate

```python
#!/usr/bin/pypy
# real	0m5.662s
# user  0m5.648s
# sys	  0m0.004s
from random import random
NUM_SAMPLES = 10**8

count_pass = 0

for _ in range(0, NUM_SAMPLES):
    x, y = random(), random()
    if (x*x + y*y <= 1):
        count_pass += 1
print(4.0 * count_pass / NUM_SAMPLES)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
