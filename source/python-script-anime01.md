---
title: python script anime01 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'anime01'


Modules used in program: 
* `import matplotlib.animation as animation`
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python anime01

Python mysql example: anime01

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

fig = plt.figure()
x = np.arange(0, 10, 0.1)

ims = []
for a in range(50):
    y = np.sin(x - a)
    im = plt.plot(x, y, "r")
    ims.append(im)

ani = animation.ArtistAnimation(fig, ims)
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
