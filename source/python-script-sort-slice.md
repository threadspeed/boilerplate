---
title: python script sort-slice (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sort-slice'


Modules used in program: 
* `import resource`

## python sort-slice

Python example: sort-slice

```python
import resource
from random import random

sorted((random() for i in xrange(1000000)), reverse=True)[:5]

print(resource.getrusage(resource.RUSAGE_SELF).ru_maxrss)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
