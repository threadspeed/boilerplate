---
title: python script render (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'render'

Functions in program: 
* `def user_input(events):`
* `def _random_color():`
* `def handleMouseClick(event):`
* `def _isLMB(event):`
* `def init_game():`
* `def update_Blobs():`
* `def game_main_loop():`
* `def main():`

Modules used in program: 
* `import blob `
* `import random`
* `import pygame`

## python render

Python example: render

```python
import pygame
import random
import blob 

input_delay = 8000 # time gap between handling user input events (in miliseconds).
WINDOW_WIDTH = 512
WINDOW_HEIGHT = 512

def main():
    """
    This function is being executed when this file is run as a main module
    """
    init_game()
    game_main_loop()
    
    
def game_main_loop():
    clock = pygame.time.Clock()
    while True:
        clock.tick(input_delay)
        events = pygame.event.get()
        user_input(events)
        update_Blobs()
        pygame.display.update()
        
        
def update_Blobs():
    for blob in blobs:
        blob.update()   
        blob.draw(window)     
        
def init_game():
    global window
    pygame.init()
    window = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
    


    
    
def _isLMB(event):
    if event.button == 1:
        return True
    else:
        return False
blobs = list()
def handleMouseClick(event):
    pos = event.pos
    radius = random.randint(10,100)
    color = _random_color()
    b = blob.FluctuatingCircle(pos,radius,color,1)
    blobs.append(b)


def _random_color():
    r = random.randint(0,255)
    g = random.randint(0,255)
    b = random.randint(0,255)
    return r,g,b


def user_input(events):
    for event in events:
        if event.type == pygame.QUIT:
            raise SystemExit
        if event.type == pygame.MOUSEBUTTONDOWN:
            handleMouseClick(event)


if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
