---
title: python script ex1 setPoint MFnMesh (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex1 setPoint MFnMesh'


Modules used in program: 
* `import random `

## python ex1 setPoint MFnMesh

Python mysql example: ex1 setPoint MFnMesh

```python
# Exapmpe1

# Apply noise to vertices using setter/getter functions in MFnMesh
# Select a single object and run this

import random 
from maya.api import OpenMaya


# API equivalent of "cmds.ls(sl=True)"
sel = OpenMaya.MGlobal.getActiveSelectionList()
dagPath = sel.getDagPath(0)
print(dagPath.fullPathName())

# Create MFnMesh class instance to edit an geometry
fnMesh = OpenMaya.MFnMesh(dagPath)

# Get points at once as MPointArray
points = fnMesh.getPoints()

# Container to store new points
pointArray = OpenMaya.MPointArray()

for p in points:
    rand_x = random.random()
    rand_y = random.random()
    rand_z = random.random()

    # Vector to random direction
    noise = OpenMaya.MVector(rand_x, rand_y, rand_z)

    # Noise intensity
    noise_intensity = 0.1

    # Point + Vector = new Point
    new_p = p + (noise * noise_intensity)

    # Append new point to the container
    pointArray.append(new_p)

# Set all points
fnMesh.setPoints(pointArray)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
