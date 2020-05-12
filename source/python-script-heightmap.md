---
title: python script heightmap (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'heightmap'

Functions in program: 
* `def get_verts_indices_for_heightmap(heightmap, stepx, stepy, minz, maxz):`

Modules used in program: 
* `import itertools`

## python heightmap

Python example: heightmap

```python
import itertools

def get_verts_indices_for_heightmap(heightmap, stepx, stepy, minz, maxz):
	""" heightmap assumed to be normalized (values between 0 and 1)
	"""
	height = len(heightmap)
	width = len(heightmap[0])
	spanz = maxz - minz

#	n_heightmap = width * height
#	n_tris = n_heightmap * 2
#	n_indices = n_tris * 3

	indices = []
	verts = []

	# the indices
	# embarassingly parallel
	for i, j in itertools.product(range(width - 1), range(height - 1))
		idx = (i * width) + j

		# 4 points of a grid cell
		a = idx
		b = idx + 1
		c = idx + width
		d = idx + width + 1

		t1 = (a, c, b)
		t2 = (b, c, d)

		indices.extend(t1)
		indices.extend(t2)

	# the vertices
	# embarassingly parallel
	for i, j in itertools.product(range(width), range(height))
		x = j * stepx
		y = i * stepy
		z = minz + (normalized_map[i][j] * spanz)

		vert = (x, y, z))
		verts.append(vert)

	return verts, indices


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
