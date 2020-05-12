---
title: python script draw (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'draw'

Functions in program: 
* `def mk_socialdata():`
* `def drawnetwork(people,links):`

Modules used in program: 
* `import socialdata as sd`
* `import random`

## python draw

Python mysql example: draw

```python
#! /usr/bin/env python

from PIL import Image, ImageDraw
import random
import socialdata as sd

def drawnetwork(people,links):
    img = Image.new('RGB',(500,500),(255,255,255))
    draw = ImageDraw.Draw(img)
    
    pos=dict(people)

    for (a,b) in links:
        draw.line((pos[a],pos[b]),fill=(255,0,0))

    for n,p in pos.items():
        draw.text(p,n,(0,0,0))

    img.show()

def mk_socialdata():
    people_num = 10
    links_loop = 15
    upper="ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    lower="abcdefghijklmnopqrstuvwxyz"

    a = 50
    b = 450
    people = [(random.choice(upper)
               +random.choice(lower)
               +random.choice(lower)
               +random.choice(lower),
               (random.randint(a,b),random.randint(a,b)))
              for x in range(people_num)]
    linkset = set([(random.choice(people)[0],random.choice(people)[0])
               for i in range(links_loop)])
    new_linkset = [x for x in linkset if len(set(x))!=1]

    return (people, new_linkset)

#if True:
if False:
    p,l = mk_socialdata()
    drawnetwork(p,l)
else:
    drawnetwork(sd.people, sd.links)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
