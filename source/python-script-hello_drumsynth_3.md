---
title: python script hello drumsynth 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hello drumsynth 3'

Functions in program: 
* `def generate(notefn,`
* `def handle_empty(fn):`

Modules used in program: 
* `import random`

## python hello drumsynth 3

Python example: hello drumsynth 3

```python
from rv.api import Project
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
             seed=13):
    random.seed(seed)
    from rv.modules.drumsynth import DrumSynth
    from rv.modules.distortion import Distortion
    from rv.modules.reverb import Reverb
    proj=Project()
    for i, Mod in enumerate([Reverb,
                             Distortion,
                             DrumSynth]):
        x=512-128*(i+1)
        proj.attach_module(Mod(x=x))
        proj.connect(proj.modules[i+1],
                     proj.modules[i])
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
            return Note(note=49,
                        module=4)
        elif j==1 and 4==i%8: # snare
            return Note(note=80,
                        module=4)
        elif j==2 and 2==i%4: # hat
            return Note(note=65,
                        module=4)
        elif j==3 and 1==i%2 and random.random() < 0.3: # tom
            return Note(note=random.choice([109, 110, 111, 112]),
                        vel=64, # NB
                        module=4)
        elif j==4 and i==54: # hiss
            return Note(note=77,
                        module=4)
        elif j==5 and 0==i%4: # distortion
            return Note(module=3,
                        ctl=3*(2**8),
                        val=int(random.random()*(2**14)))
        elif j==6 and 0==i%8: # reverb
            return Note(module=2,
                        ctl=2*(2**8),
                        val=int(random.random()*(2**11)))
    generate(notefn,
             filename="hello_drumsynth_3.sunvox",
             seed=14,
             tracks=7)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
