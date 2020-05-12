---
title: python script timing beat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'timing beat'

Functions in program: 
* `def reset():`
* `def resume():`
* `def pause():`

Modules used in program: 
* `import operator`
* `import random`

## python timing beat

Python mysql example: timing beat

```python
import random
import operator

from itertools import permutations

from bl.scheduler import clock, Tempo  # , Meter
from bl.arp import RandomArp, OrderedArp, ScheduleArp  # , ArpSwitcher
from bl.orchestra.midi import Player

from tutor.complib import drums_f


clock.setTempo(Tempo(90))

drums = drums_f()

eifs = [list(t) for t in
        list(permutations([(1, 8), (0, 8)], 1))
]
teenfs = [list(t) for t in
          list(set(permutations([(1, 16), (0, 16)] * 2, 2)))
]
#turdysekondz = [list(t) for t in
#                list(set(permutations([(1, 32), (0, 32)] * 4, 4)))
#]

turdysekondz = [
    [(1, 32)] * 4
]

teenz = eifs + teenfs
allz = eifs + teenfs + turdysekondz

ti = reduce(operator.add, [random.choice(allz) for i in range(8)])
ti2 = reduce(operator.add, [random.choice(teenz) for i in range(8)])
ti3 = reduce(operator.add, [random.choice(allz) for i in range(4)])
ti4 = reduce(operator.add, [random.choice(allz) for i in range(4)])
ti5 = reduce(operator.add, [random.choice(allz) for i in range(3)])
ti6 = reduce(operator.add, [random.choice(teenz) for i in range(8)])
ti7 = reduce(operator.add, [random.choice(teenz) for i in range(5)])


dhats = Player(drums,
    note=OrderedArp([42]),
    velocity=OrderedArp([127]),
    time=ScheduleArp(ti)
)
dhats.resumePlaying()

cym = Player(drums,
    note=OrderedArp([44, 46]),
    velocity=RandomArp(range(70, 100)),
    time=ScheduleArp(ti2)

)
cym.resumePlaying()

cym2 = Player(drums,
    note=OrderedArp([51, 53, 59]),
    velocity=RandomArp(range(70, 100)),
    time=ScheduleArp(ti7),
)
cym2.resumePlaying()

bump = Player(drums,
    note=OrderedArp([45]),
    velocity=OrderedArp([127]),
    time=ScheduleArp(ti3),
)
bump.resumePlaying()

bump2 = Player(drums,
    note=OrderedArp([43, 35, 36, 47]),
    velocity=RandomArp(range(100, 127)),
    time=ScheduleArp(ti6),
)
bump2.resumePlaying()

snare = Player(drums,
    note=RandomArp([39, 38, 37, 40]),
    velocity=RandomArp(range(100, 127)),
    time=ScheduleArp(ti4),
)
snare.resumePlaying()

conga = Player(drums,
    note=RandomArp(range(60, 66)),
    velocity=RandomArp(range(70, 120)),
    time=ScheduleArp(ti5)
)
conga.resumePlaying()


def pause():
    dhats.pausePlaying()
    cym.pausePlaying()
    cym2.pausePlaying()
    bump.pausePlaying()
    bump2.pausePlaying()
    snare.pausePlaying()
    conga.pausePlaying()


def resume():
    dhats.resumePlaying()
    cym.resumePlaying()
    cym2.resumePlaying()
    bump.resumePlaying()
    bump2.resumePlaying()
    snare.resumePlaying()
    conga.resumePlaying()


def reset():
    for p in dhats, cym, cym2, bump, bump2, snare, conga:
        choice = random.choice([allz, teenz])
        p.time.reset(reduce(
            operator.add, [random.choice(choice)
                           for i in range(random.randint(2, 8))]
        ))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
