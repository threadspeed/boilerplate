---
title: python script hemligtomte (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hemligtomte'


Modules used in program: 
* `import sys`
* `import random`

## python hemligtomte

Python mysql example: hemligtomte

```python
# -*- coding: utf-8 -*-

import random
import sys

xlist = list(sys.argv)
xlist.remove('hemligtomte.py')

tomtarInput = list(xlist)
mottagareInput = list(xlist)

kontroll = True


while kontroll == True:

  tomtar = list(tomtarInput)
  mottagare = list(mottagareInput)
  mottagareSlump = []
  resultat = []

  for i in range (len(mottagare)):
    temp = random.choice(mottagare)
    mottagareSlump.append(temp)
    mottagare.remove(temp)

  for i in range (len(mottagareSlump)):
    if tomtar[i] == mottagareSlump[i]:
      kontroll = True
      break
    else:
      kontroll = False



print('')
for i in range (len(mottagareSlump)):
  print((tomtar[i] + ' är hemlig tomte åt ' + mottagareSlump[i]))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
