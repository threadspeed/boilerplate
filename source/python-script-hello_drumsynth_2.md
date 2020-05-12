---
title: python script hello drumsynth 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hello drumsynth 2'

Functions in program: 
* `def generate(notefn,`
* `def handle_empty(fn):`

Modules used in program: 
* `import random`

## python hello drumsynth 2

Python mysql example: hello drumsynth 2

```python
from rv.api import Project
from rv.modules.drumsynth import DrumSynth
from rv.pattern import Pattern
from rv.note import Note

import random

def handle_empty(fn):
    def wrapped(*args, **kwargs):
        resp=fn(*args, **kwargs)
        return Note() if not resp else resp
    return wrapped

def generate(notefn,
             filename,             
             lines=64,
             tracks=1,
             x=256,
             seed=13):
    random.seed(seed)
    proj=Project()
    drum=DrumSynth(x=x)
    proj.attach_module(drum)
    proj.connect(proj.modules[1],
                 proj.modules[0])
    pat=Pattern(lines=lines,
                tracks=tracks)
    pat.set_via_fn(notefn)
    proj.patterns.append(pat)
    with open(filename, 'wb') as f:
        proj.write_to(f)
    
if __name__=="__main__":
    @handle_empty
    def notefn(track, i, j):
        if j==0 and 0==i%4: # bass
            return Note(note=49, module=2)
        elif j==1 and 4==i%8: # snare
            return Note(note=80, module=2)
        elif j==2 and 2==i%4: # hat
            return Note(note=65, module=2)
        elif j==3 and 1==i%2 and random.random() < 0.3: # tom
            return Note(note=random.choice([109, 110, 111, 112]), module=2)
        elif j==4 and i==54: # hiss
            return Note(note=77, module=2)
    generate(notefn,
             filename="hello_drumsynth_2.sunvox",
             seed=14,
             tracks=5)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
