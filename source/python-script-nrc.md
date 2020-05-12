---
title: python script nrc (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nrc'


Modules used in program: 
* `import os`
* `import random`
* `import nuke`
* `import random`
* `import nuke`

## python nrc

Python mysql example: nrc

```python
# limited random scaling
import nuke
import random

min_scale = 800
max_scale = 1600

for node in nuke.selectedNodes("Card2"):
    scale = random.uniform(min_scale, max_scale)
    node['uniform_scale'].setValue(scale)

# random image in folder
import nuke
import random
import os

for node in nuke.selectedNodes("Read"):
    path = node['file'].getValue()
    root = os.path.dirname(path)

    images = []
    for f in os.listdir(root):
        images.append(f)
    
    f = random.choice(images)
    new_path = os.path.join(root, f).replace('\\', '/')
    node['file'].setValue(new_path)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
