---
title: python script ex4 iterateOnlySelectedVertices (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex4 iterateOnlySelectedVertices'


Modules used in program: 
* `import random `

## python ex4 iterateOnlySelectedVertices

Python example: ex4 iterateOnlySelectedVertices

```python
# Example 4
# Push only selected vertices along normal direction


from maya.api import OpenMaya
import random 


sel = OpenMaya.MGlobal.getActiveSelectionList()
dagPath, mObj = sel.getComponent(0)

itVerts = OpenMaya.MItMeshVertex(dagPath, mObj)


fnMesh = OpenMaya.MFnMesh(dagPath)

pointArray = fnMesh.getPoints()

while not itVerts.isDone():

    # Get current point postion as MPoint
    point = itVerts.position()
    normal = itVerts.getNormal()

    pointID = itVerts.index()

    normal_intensity = 0.1

    new_p = point + (normal * normal_intensity )

    pointArray[pointID] = new_p

    itVerts.next() # <- Never ever forget this line otherwise maya freezes by infinite loop


fnMesh.setPoints(pointArray)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
