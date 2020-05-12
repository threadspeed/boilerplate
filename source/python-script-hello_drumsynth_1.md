---
title: python script hello drumsynth 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hello drumsynth 1'


## python hello drumsynth 1

Python mysql example: hello drumsynth 1

```python
from rv.api import Project
from rv.modules.drumsynth import DrumSynth
from rv.pattern import Pattern
from rv.note import Note

if __name__=="__main__":
    proj=Project()
    drum=DrumSynth(x=256)
    proj.attach_module(drum)
    proj.connect(proj.modules[1],
                 proj.modules[0])
    pat=Pattern(lines=64,
                tracks=1)
    def notefn(track, i, j):
        if 0==i%4:
            return Note(note=1,
                        module=2)
        else:
            return Note()
    pat.set_via_fn(notefn)
    proj.patterns.append(pat)
    with open("hello_drumsynth_1.sunvox", 'wb') as f:
        proj.write_to(f)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
