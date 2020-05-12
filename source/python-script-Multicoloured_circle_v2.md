---
title: python script Multicoloured circle v2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Multicoloured circle v2'

Functions in program: 
* `def main():`
* `def r(win):`
* `def drawCircle(center: Point, radius: int):`

Modules used in program: 
* `import math`
* `import random`

## python Multicoloured circle v2

Python example: Multicoloured circle v2

```python
from graphics import *
import random
import math

def drawCircle(center: Point, radius: int):
    lines=[]
    for i in range(1, 181):
        p1 = Point(center.x+((radius * math.cos(math.radians(i)))),center.y+((radius * math.sin(math.radians(i)))))
        p2 = Point(center.x + ((radius * math.cos(math.radians(360 - i)))), center.y + ((radius * math.sin(math.radians(360 - i)))))
        newLine = Line(p1, p2)
        lines.append(newLine)
    return lines
    
def r(win):
    lines= drawCircle(Point(250,250), 100)
    for line in lines:
        line.setOutline('#%06X' % random.randint(0, 0xFFFFFF))
        line.draw(win)
    
    win.getMouse()


def main():
    win = GraphWin('r', 500,500)
    r(win)

if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
