---
title: python script directory index (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'directory index'

Functions in program: 
* `def showfile(file, indent, path):`

Modules used in program: 
* `import os.path`
* `import os`

## python directory index

Python mysql example: directory index

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

import os
import os.path

def showfile(file, indent, path):
  if file[0] != '.':
    next = path + "/" + file
    if os.path.exists(next):
      if os.path.isfile(next) :
        for x in range(0, indent):
          print(" ",)
        print('<a href="' + file + '>' + file + '</a>    ')
      else:
        print('<a href="' + file + '/' + '>' + file + '/' + '</a>    ')
        directory = os.listdir(next)
        for x in directory:
          showfile(x, indent + 1, next)

print('<html>\n  <body>\n    <h1>Index of /</h1>\n    <hr>\n    <pre>    ')
list = os.listdir(os.getcwd())
for file in list:
  showfile(file, 0, os.getcwd())
print('</pre>\n  </body>\n<html>')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
