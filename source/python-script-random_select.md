---
title: python script random select (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random select'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python random select

Python example: random select

```python
#!/usr/bin/python
# -*- coding:utf-8 -*-

import random

def main():
  all=["@a","@b","@c","@d","@e","@f"]
  copy_all=all[:]
  results=[]
  for i in range(2):
    t=random.choice(copy_all)
    results.append(t)
    copy_all.remove(t)

  print(results)

if __name__ == '__main__':
  main()
# [結果]
# ['@e', '@b']


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
