---
title: python script worker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'worker'

Functions in program: 
* `def slow_pow(i):`

Modules used in program: 
* `import math`
* `import random`
* `import time`
* `import os`

## python worker

Python mysql example: worker

```python
import os
import time
import random
import math
from rq import Queue, Connection

def slow_pow(i):
	t = random.randint(5,20)
	time.sleep(t)
	return math.pow(i, 2)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
