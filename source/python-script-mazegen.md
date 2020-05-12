---
title: python script mazegen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mazegen'

Functions in program: 
* `def genmaze(xcells, ycells):`
* `def dispcellmap(cells):`

Modules used in program: 
* `import random`

## python mazegen

Python example: mazegen

```python
import random

class Cell(object):
    def __init__(self, x, y, visited=False, content=' ', walls=None):
        self.visited = visited
        self.x = x
        self.y = y
        if walls == None:
            self.walls = [(1,0), (-1,0), (0,1), (0,-1)]
        else:
            self.walls = walls
        self.content = content
    
    def walk(self, stack, context):
        self.visited = True
        choicelist = self.walls.copy()
        if len(choicelist) == 0:
            return None
        (dx, dy) = random.choice(choicelist)
        while context[self.y + dy][self.x + dx].visited:
            choicelist.remove((dx, dy))
            if len(choicelist) == 0:
                return None
            (dx, dy) = random.choice(choicelist)
        self.walls.remove((dx,dy))
        context[self.y + dy][self.x + dx].walls.remove((-dx, -dy))
        stack.append(self)
        return context[self.y + dy][self.x + dx]


def dispcellmap(cells):
    xlength = len(cells[0])*2 - 3 # = (len(cells[0]) - 2)*2 + 1
    dispmap = ['#'*xlength]
    for line in cells[1:-1]:
        if (-1,0) in line[1].walls:
            newline = '#'
        else:
            newline = ' '
        newline2 = '#'
        for cell in line[1:-1]:
            newline += cell.content
            if (1,0) in cell.walls:
                newline += '#'
            else:
                newline += ' '
            if (0,1) in cell.walls:
                newline2 += '##'
            else:
                newline2 += ' #'
        dispmap.append(newline)
        dispmap.append(newline2)
    return '\n'.join(dispmap)
       

def genmaze(xcells, ycells):
    cellmap = [[Cell(x, y) for x in range(xcells+2)] for y in range(ycells+2)]
    for bordercell in cellmap[0] + cellmap[-1]:
        bordercell.visited = True
    for line in cellmap:
        line[0].visited = True
        line[-1].visited = True
    currcell = random.choice(random.choice(cellmap[1:-1])[1:-1])
    currcell.content = 'X'
    stack = []
    newcell = currcell.walk(stack, cellmap)
    while newcell or len(stack) > 0:
        if newcell:
            currcell = newcell
        else:
            currcell = stack.pop()
        newcell = currcell.walk(stack, cellmap)
    return dispcellmap(cellmap)

if __name__ == "__main__":
    print(genmaze(10, 10))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
