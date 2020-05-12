---
title: python script fast reservoir sampling (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fast reservoir sampling'

Functions in program: 
* `def fast_reservoir_sampling(file_handle, N=1000000, callable=None):`

Modules used in program: 
* `import numpy as np`
* `import random`

## python fast reservoir sampling

Python example: fast reservoir sampling

```python
import random
import numpy as np
# http://erikerlandson.github.io/blog/2015/11/20/very-fast-reservoir-sampling/
def fast_reservoir_sampling(file_handle, N=1000000, callable=None):
    sample = []

    if callable is None:
        callable = lambda x: x

    j = N
    for n, line in enumerate(file_handle):
        if n < N:
            sample.append(callable(line))
        else:
            if n < j:
                continue
            p = N / n
            g = np.random.geometric(p)
            j = j + g
            replace = random.randint(0, N-1)
            sample[replace] = callable(line)

    return sample

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
