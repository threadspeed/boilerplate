---
title: python script hex color between (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hex color between'


Modules used in program: 
* `import sys`

## python hex color between

Python example: hex color between

```python
# coding: utf-8

import sys

argv = sys.argv
argc = len(argv)

if (argc != 3) :
  print("python hex_color_between.py AAAAAA CCCCCC")
  quit()
  
color1 = argv[1]
color2 = argv[2]

if (len(color1) != 6):
  print("input error")
  quit()

if (len(color2) != 6):
  print("input error")
  quit()

result1 = (int(color1[0:2], 16) + int(color2[0:2], 16)) / 2
result2 = (int(color1[2:4], 16) + int(color2[2:4], 16)) / 2
result3 = (int(color1[4:6], 16) + int(color2[4:6], 16)) / 2

print("#" + "%x" % result1 + "%x" % result2 + "%x" % result3)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
