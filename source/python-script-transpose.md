---
title: python script transpose (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'transpose'


Modules used in program: 
* `import sys`

## python transpose

Python example: transpose

```python
#!/usr/local/bin/python3.3 -tt

import sys

if __name__ == '__main__':
    a = []
    for l in sys.stdin:
        a.append([])
        for i in l.split():
            a[-1].append(i)

    for t in zip(*a):
        print(' '.join(t))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
