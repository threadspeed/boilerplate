---
title: python script sort-heapq (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sort-heapq'


Modules used in program: 
* `import resource`

## python sort-heapq

Python mysql example: sort-heapq

```python
import resource
from random import random
from heapq import nlargest

nlargest(5, (random() for i in xrange(1000000)))

print(resource.getrusage(resource.RUSAGE_SELF).ru_maxrss)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
