---
title: python script game-of-life-first-pass (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'game-of-life-first-pass'


Modules used in program: 
* `import random, time`

## python game-of-life-first-pass

Python mysql example: game-of-life-first-pass

```python
# Conway's Game of Life

import random, time
WIDTH = 80
HEIGHT = 40

class Cell:
    def __init__(self, alive = None):
        self.alive = alive if alive is not None else random.randint(0, 1) == 0
        self.nextAlive = alive
        self.neighbors = []
        self.livingNeighbors = 0
        
    # Set cell based on Conway's Game of Life Rules
    def printAndUpdate(self):
        print("#" if self.alive else " ", end="")

        if self.alive:
            # Update neighbor cells' living neighbor counts
            for neighbor in self.neighbors:
                neighbor.livingNeighbors += 1


    def cycle(self):
        changed = False
        if self.alive:
            if self.livingNeighbors != 2 and self.livingNeighbors != 3:
                # Living cells with < 2 or > 3 neighbors die:
                self.alive = False
                changed = True
        elif self.livingNeighbors == 3:
            # Dead cells with 3 neighbors become alive:
            self.alive = True
            changed = True

        self.livingNeighbors = 0
        return changed
            
cells = [[Cell() for y in range(HEIGHT)] for x in range(WIDTH)]

# Set up neighbor references
for x in range(WIDTH):
    for y in range(HEIGHT):
        cell = cells[x][y]
        for xOff in range(-1, 2): #-1, 0, 1
            for yOff in range (-1, 2): #-1, 0, 1
                # Don't add ourselves
                if xOff != 0 or yOff != 0:
                    # Wrap our neigbor coordinates using modulo math
                    nx = (x + xOff) % WIDTH
                    ny = (y + yOff) % HEIGHT
                    cell.neighbors.append(cells[nx][ny])

iteration = 1
while True: # Main program loop
    print(f"Iteration: {iteration}")
    for y in range(HEIGHT):
        for x in range(WIDTH):
            cells[x][y].printAndUpdate()
        print()
    
    for x in range(WIDTH):
        for y in range(HEIGHT):
            cells[x][y].cycle()

    time.sleep(0.1)

    # Return our cursor to the top
    print("\033[F" * (HEIGHT + 2))
    iteration += 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
