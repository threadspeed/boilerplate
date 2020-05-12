---
title: python script ex2 setPoint MItMeshVertex (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex2 setPoint MItMeshVertex'


Modules used in program: 
* `import random `

## python ex2 setPoint MItMeshVertex

Python mysql example: ex2 setPoint MItMeshVertex

```python
# Exapmle2

# Apply noise to vertices using setter/getter functions in mesh interater
# Select a single object and run this

# ### IMPORTANT ###
# Getting/Setting point one by one in iterator is way slower than setting once
# using MFnMesh.setPoints function. Try setPoints first if possible.
# #################


from maya.api import OpenMaya
import random 


sel = OpenMaya.MGlobal.getActiveSelectionList()
dagPath = sel.getDagPath(0)

itVerts = OpenMaya.MItMeshVertex(dagPath)

while not itVerts.isDone():

    # Get current point postion as MPoint
    p = itVerts.position()

    rand_x = random.random()
    rand_y = random.random()
    rand_z = random.random()

    # Create random vector
    noise = OpenMaya.MVector(rand_x, rand_y, rand_z)
    noise_intensity = 0.1

    new_p = p + (noise * noise_intensity )

    itVerts.setPosition(new_p)
    itVerts.next() # <- Never ever forget this line otherwise maya freezes by infinite loop


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
