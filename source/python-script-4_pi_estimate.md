---
title: python script 4 pi estimate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '4 pi estimate'


## python 4 pi estimate

Python mysql example: 4 pi estimate

```python
#!/usr/bin/python3
# Execution time for 10e8
# real	0m52.483s
# user	0m52.244s
# sys	0m0.024s
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
