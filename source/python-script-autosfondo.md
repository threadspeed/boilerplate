---
title: python script autosfondo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'autosfondo'


Modules used in program: 
* `import random`

## python autosfondo

Python mysql example: autosfondo

```python
from PIL import Image, ImageDraw
import random

i = Image.new('RGB', (1600, 900))
d = ImageDraw.Draw(i)
for y in range(0, 900):
    for x in range(0, 1600):
        rosso = random.normalvariate(33, 32)
        verde = random.normalvariate(33, 32)
        blu = random.normalvariate(33, 32)
        d.point((x, y), (int(rosso), int(verde), int(blu)))
    if not y % 100:
        print(str(int(y * 100 / 900)) + "%")
print("100%")
del d
i.save("sfondo.png")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
