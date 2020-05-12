---
title: python script randomHuslColor (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randomHuslColor'


Modules used in program: 
* `import random`

## python randomHuslColor

Python example: randomHuslColor

```python
from husl import husl_to_rgb
import random

font = CurrentFont()

golden_ratio_conjugate = 0.618033988749895

h = random.random()
minS = random.uniform(30, 70)
maxS = minS + 30
minL = random.uniform(50, 70)
maxL = minL + 20

print(minS, minL)

for glyph in font:
    glyph.prepareUndo()
    h = (h + golden_ratio_conjugate) % 1
    hue = 360 * h
    sat = random.uniform(minS, maxS)
    lum = random.uniform(minL, maxL)
    col = husl_to_rgb(hue, sat, lum) + [1]
    color = ",".join(str(c) for c in col)
    glyph.lib["public.markColor"] = color

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
