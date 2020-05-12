---
title: python script ex3 transferVertexPosition (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex3 transferVertexPosition'


Modules used in program: 
* `import random `

## python ex3 transferVertexPosition

Python mysql example: ex3 transferVertexPosition

```python
# Exapmpe3

# Transfer vertex position using getter/setter function in MFnMesh 
# Select two objects and run this

import random 
from maya.api import OpenMaya


# API equivalent of "cmds.ls(sl=True)"
sel = OpenMaya.MGlobal.getActiveSelectionList()
sourceDagPath = sel.getDagPath(0)  # First selection
targetDagPath = sel.getDagPath(1)  # Second selection

# Create MFnMesh class instance for source mesh
sourceFnMesh = OpenMaya.MFnMesh(sourceDagPath)

# Create MFnMesh class instance for target mesh
targetFnMesh = OpenMaya.MFnMesh(targetDagPath)

# # Get points for source mesh
sourcePoints = sourceFnMesh.getPoints()

# Copy/Apply source point positions to target mesh
targetFnMesh.setPoints(sourcePoints)

# By default, this transfer point positions by "Object space"
# If you want to copy in different space, you have to specify as argments.
# FOR BOTH GETTER AND SETTER
# OpenMaya.MSpace.kObject
# OpenMaya.MSpace.kWorld

# For example, in world space
# sourcePoints = sourceFnMesh.getPoints(OpenMaya.MSpace.kWorld)
# targetFnMesh.setPoints(sourcePoints, OpenMaya.MSpace.kWorld)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
