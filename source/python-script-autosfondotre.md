---
title: python script autosfondotre (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'autosfondotre'


Modules used in program: 
* `import random`

## python autosfondotre

Python mysql example: autosfondotre

```python
from PIL import Image, ImageDraw
import random

i = Image.new('RGB', (1600, 900), (0, 0, 0))
d = ImageDraw.Draw(i)

for y in range(0, 900):
    for x in range(0, 1600):
        d.point((x, y), (x % 2 * 255, y % 2 * 255, int(x * y / (1600 * 900) * 255)))

i.save("sfondo.png")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
