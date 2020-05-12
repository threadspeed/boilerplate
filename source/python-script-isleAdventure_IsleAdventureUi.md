---
title: python script isleAdventure IsleAdventureUi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'isleAdventure IsleAdventureUi'

Functions in program: 
* `def quit_game():`

Modules used in program: 
* `import pygame`

## python isleAdventure IsleAdventureUi

Python mysql example: isleAdventure IsleAdventureUi

```python
#set up
import pygame
BLACK = (0, 0, 0)
WHITE = (255,255,255)
RED = (255, 0, 0)
GREEN = (13, 255, 0)
YELLOW = (0, 255, 20)
BRIGHT_YELLOW = (255, 255, 20)
s = int(input(print("Hello do you want to use the default display size of 800 by 600?\ntype 1 for yes and 2 for no")))

if s == 1:
    game_display = pygame.display.set_mode((800, 600))
    print("Enjoy the game player")
    surface = pygame.Surface((800, 600))
if s == 2:
    X = int(input(print("What is your 'X' resolution?")))
    Y = int(input(print("What is your 'Y' resolution?")))
    game_display = pygame.display.set_mode((X, Y))
    print("Enjoy the game player")
    surface = pygame.Surface((X, Y))
pygame.init()
#Game start
done = False
while not done:
        for event in pygame.event.get():
                if event.type == pygame.QUIT:
                        done = True

def quit_game():
    pygame.quit()
    sys.exit()
#Screens
def Mainmenu






```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
