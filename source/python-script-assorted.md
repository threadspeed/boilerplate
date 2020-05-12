---
title: python script assorted (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'assorted'

Functions in program: 
* `def unzip(iterable):`
* `def group(iterable, key=lambda x:x):`
* `def stamp(canvas, coord, brush, out=None):`
* `def random_crop_slice(input_shape, target_shape,rand=random):`

Modules used in program: 
* `import numpy as np`
* `import random`

## python assorted

Python example: assorted

```python
# generate slices of extent target_shape for indexing object of shape input_shape
import random
def random_crop_slice(input_shape, target_shape,rand=random):
    dim_pairs = list(zip(input_shape,target_shape))
    assert not any([s-c < 0 for s, c in dim_pairs]) 
    starts = [rand.randrange(s-c) if s-c > 0 else 0 for s,c in dim_pairs]
    slices = [slice(s, s+c) for s, c in zip(starts, target_shape)]
    return slices


# stamp a numpy array into another numpy array by finding overlapping region
import numpy as np

def stamp(canvas, coord, brush, out=None):
    if out is None:
        out = np.array(canvas)
    canvas = out

    centre = [int(round(a)) for a in coord]
    # top left and bottom right
    start_coords = [c - brush_shape//2 for c, brush_shape in zip(centre, brush.shape)]
    end_coords = [c + brush_shape//2 for c, brush_shape in zip(centre, brush.shape)]

    brush_start = [0,0]
    brush_end = [e - 1 for e in brush.shape]

    for i, start_coord in enumerate(start_coords):
        if start_coord < 0:
            start_coords[i] = 0
            brush_start[i] -= start_coord
    for i, end_coord in enumerate(end_coords):
        if end_coord >= canvas.shape[i]:
            end_coords[i] = canvas.shape[i]
            brush_end[i] += canvas.shape[i] - end_coord

    stamp = brush[brush_start[0]:brush_end[0],
                  brush_start[1]:brush_end[1]]

    canvas[start_coords[0]:end_coords[0],
           start_coords[1]:end_coords[1]] = stamp
    return canvas

# generic function for applying a list of functions to a single input
# useful for applying lists of Keras layers to an input
from functools import reduce
identity = lambda x:x
compose = lambda f, g: lambda x: f(g(x))
apply = lambda f, x: f(x)
flip = lambda f: lambda a, b: f(b, a)
apply_sequence = lambda l, x: reduce(flip(apply), l, x)

# apply function f to first element of container a
# e.g. map(fst(type),[("a",1),(1,"a")]) -> [(str,1),(int,"a")]
fst = lambda f: lambda a: type(a)((f(a[0]),)) + a[1:]

from collections import defaultdict
def group(iterable, key=lambda x:x):
    d = defaultdict(list)
    for x in iterable:
        d[key(x)].append(x)
    return d.values()

def unzip(iterable):
    return zip(*iterable)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
