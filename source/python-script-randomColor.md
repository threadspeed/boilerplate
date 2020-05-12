---
title: python script randomColor (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randomColor'


Modules used in program: 
* `import random`

## python randomColor

Python mysql example: randomColor

```python
import random

font = CurrentFont()

for glyph in font:
    glyph.prepareUndo()
    color = ",".join(str(random.random()) for _ in range(4))
    glyph.lib["public.markColor"] = color

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
