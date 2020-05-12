---
title: python script Game Stuff an example directory basic loop (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Game Stuff an example directory basic loop'

Functions in program: 
* `def exit():`

Modules used in program: 
* `import sys`
* `import pygame`

## python Game Stuff an example directory basic loop

Python example: Game Stuff an example directory basic loop

```python

import pygame
import sys
from pygame.locals import *
pygame.init()

# set up the window

DISPLAY_SURFACE = pygame.display.set_mode((256, 256), 0, 32)
pygame.display.set_caption('Basic Blank screen loop')

clock = pygame.time.Clock()
# run the game loop

def exit():
    pygame.display.quit()
    pygame.quit()
    sys.exit()

alive = True
while alive:
    for event in pygame.event.get():
        if event.type == QUIT:
            alive = False

        print(event)

    pygame.display.update()
    clock.tick(60)  # keep 60 fps
exit()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
