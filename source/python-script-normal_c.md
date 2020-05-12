---
title: python script normal c (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'normal c'


Modules used in program: 
* `import numpy as np`

## python normal c

Python example: normal c

```python
from math import sqrt
import numpy as np

class normal_c (object):
    def __init__ (self, rs, mean, var):
        self.rs = rs
        self.mean = mean
        self.std = sqrt (var)
        try:
            self.rs.normal (self.mean, self.std, 1, method='zig')
            self.has_zig = True
        except:
            self.has_zig = False

    def __call__ (self, size=1, dtype=complex):
        out = np.empty (size, dtype=dtype)
        if self.has_zig:
            out.real = self.rs.normal (self.mean, self.std, size, method='zig')
            out.imag = self.rs.normal (self.mean, self.std, size, method='zig')
        else:
            out.real = self.rs.normal (self.mean, self.std, size)
            out.imag = self.rs.normal (self.mean, self.std, size)
        return out



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
