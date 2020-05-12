---
title: python script game script (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game script'

Functions in program: 
* `def move_random(random_generator=random):`
* `def get_move_command(direction: Direction):`

Modules used in program: 
* `import random`

## python game script

Python mysql example: game script

```python
import random
from enum import Enum


class Direction(Enum):
    NORTH = 'north'
    SOUTH = 'south'
    EAST = 'east'
    WEST = 'west'


def get_move_command(direction: Direction):
    return {'action': 'move', 'direction': direction.value}


def move_random(random_generator=random):
    return get_move_command(random_generator.choice([direction for direction in Direction]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
