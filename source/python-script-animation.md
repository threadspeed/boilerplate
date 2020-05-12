---
title: python script animation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'animation'

Functions in program: 
* `def main():`
* `def dis(x, y):`

Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import matplotlib.animation as animation`
* `import random`

## python animation

Python mysql example: animation

```python
# coding:utf-8
from __future__ import division

import random

import matplotlib.animation as animation
import matplotlib.pyplot as plt
import numpy as np


def dis(x, y):
    return np.sqrt(x**2 + y**2)


def main():
    M = int(4e4)
    inner_x = np.zeros(M)
    inner_y = np.zeros(M)
    outer_x = np.zeros(M)
    outer_y = np.zeros(M)
    count_inner = count_outer = 0
    fig = plt.figure()
    ims =[]
    count = 0
    for n in range(M):
        x = random.random()
        y = random.random()
        if dis(x, y) < 1:
            inner_x[count_inner] = x
            inner_y[count_inner] = y
            count_inner += 1
        else:
            outer_x[count_outer] = x
            outer_y[count_outer] = y
            count_outer += 1
        if count >= M / 10 ** 2:
            im = (
                plt.scatter(
                  inner_x[:count_inner], inner_y[:count_inner],
                  c='r', marker='.', s=1),
                plt.scatter(
                  outer_x[:count_outer], outer_y[:count_outer],
                  c='b', marker='.', s=1),
                plt.text(-0.2, 0, '$n=$%5d' % n),
                plt.text(
                  -0.2, -0.035, '$\pi \\approx$%.7f' % (count_inner / n * 4)))
            ims.append(im)
            count = 0
        count += 1
    im_ani = animation.ArtistAnimation(fig, ims, interval=50, blit=True)
    plt.axis('equal')
    plt.show()


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
