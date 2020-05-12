---
title: python script sys-path-example-1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sys-path-example-1'


Modules used in program: 
* `import random # oops!`
* `import sample`
* `import sys`

## python sys-path-example-1

Python example: sys-path-example-1

```python
import sys

print("path has", len(sys.path), "members")

# add the sample directory to the path
sys.path.insert(0, "samples")
import sample

# nuke the path
sys.path = []
import random # oops!

## path has 7 members
## this is the sample module!
## Traceback (innermost last):
##   File "sys-path-example-1.py", line 11, in ?
##     import random # oops!
## ImportError: No module named random


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
