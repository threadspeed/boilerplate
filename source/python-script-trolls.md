---
title: python script trolls (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'trolls'

Functions in program: 
* `def display(maze, characters):`

Modules used in program: 
* `import mazegen`
* `import random`
* `import msvcrt`
* `import os`

## python trolls

Python mysql example: trolls

```python
import os
import msvcrt
import random
import mazegen

NUMTROLLS = 3
MAZEX = 10
MAZEY = 10

mazein = mazegen.genmaze(MAZEX, MAZEY)

mazegrid = mazein.splitlines()

dirdict = {b'H': 0, #up
    b'P': 1, #down
    b'K': 2, #left
    b'M': 3} #right

class Player(object):
    
    chars = ('^', 'v', '<', '>')
    movdirdict = {0 : (0, -1), # (x, y)
        1 : (0, 1),
        2 : (-1, 0),
        3 : (1, 0)} 
    winner = False

    def __init__(self, x, y, direction=0):
        self.x = x
        self.y = y
        self.direction = direction
    
    def __str__(self):
        return self.chars[self.direction]  

    def move(self, dir, maze):
        if dir == self.direction:
            dx, dy = self.movdirdict[dir]
            nbx, nby = self.x + 2*dx, self.y + 2*dy
            if not maze[self.y + dy][self.x + dx] == '#':
                self.y = self.y + dy
                self.x = self.x + dx
                if maze[self.y][self.x] == 'X':
                    self.winner = True
                return None
            elif nby >= 0 and nby < len(maze) and nbx >= 0 and nbx < len(maze[nby]) and maze[nby][nbx] == ' ':
                self.y = self.y + dy
                self.x = self.x + dx
                return (self.x + dx, self.y + dy)
        else:
            self.direction = dir
            return None

class Enemy(object):

    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return '&'

    def move(self, maze, target):
        xdist = target.x - self.x
        ydist = target.x - self.x
        directions = [(1,0), (0,1), (-1,0), (0,-1)]
        choices = []
        if ydist != 0:
            tup = (0, ydist//abs(ydist))
            choices.append(tup)
            directions.remove(tup)
        if xdist != 0:
            tup = (xdist//abs(xdist), 0)
            choices.append(tup)
            directions.remove(tup)
        stuck = False
        if len(choices) == 0:
            choices = directions
            stuck = True
        dx, dy = random.choice(choices)
        while maze[self.y + dy][self.x + dx] in ('#', 'X'):
            choices.remove((dx, dy))
            if len(choices) == 0 and not stuck:
                choices = directions
                stuck = True
            if len(choices) == 0 and stuck:
                dx, dy = 0, 0
            else:
                dx, dy = random.choice(choices)
            
        self.x = self.x + dx
        self.y = self.y + dy

def display(maze, characters):
    tempmaze = [list(line) for line in maze]
    os.system('cls')
    for character in characters:
        tempmaze[character.y][character.x] = str(character)
    print('\n'.join([''.join(line) for line in tempmaze]))

startx, starty = 0,0
while mazegrid[starty][startx] != ' ':
    starty = random.randint(0, len(mazegrid) - 1)
    startx = random.randint(0, len(mazegrid[starty]) - 1)
    startdir = random.randint(0, 3)

trollposlist = []
for i in range(NUMTROLLS):
    trollx, trolly = 0, 0
    while mazegrid[trolly][trollx] != ' ' or (trollx, trolly) == (startx, starty):
        trolly = random.randint(0, len(mazegrid) - 1)
        trollx = random.randint(0, len(mazegrid[trolly]) - 1)
    trollposlist.append((trollx, trolly))


player = Player(startx, starty, startdir)
trolllist = [Enemy(x, y) for (x, y) in trollposlist]

charlist = [player] + trolllist


display(mazegrid, charlist)

while True:
    if msvcrt.getch() in (b'\xe0', b'\x00'):
        newwall = player.move(dirdict[msvcrt.getch()], mazegrid)
        if newwall:
            tempgrid = [list(line) for line in mazegrid]
            tempgrid[player.y][player.x] = ' '
            tempgrid[newwall[1]][newwall[0]] = '#'
            mazegrid = [''.join(line) for line in tempgrid]
            for troll in trolllist:
                if (troll.x, troll.y) == newwall:
                    trolllist.remove(troll)
                    charlist.remove(troll)
        for troll in trolllist:
            troll.move(mazegrid, player)
            if (troll.x, troll.y) == (player.x, player.y):
                display(mazegrid, charlist)
                print("You died!")
                exit()
        display(mazegrid, charlist)
        if player.winner:
            print("You're winner!")
            exit()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
