---
title: python script Multicoloured circle (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Multicoloured circle'

Functions in program: 
* `def main():`
* `def r(win, n):`

Modules used in program: 
* `import math`
* `import random`

## python Multicoloured circle

Python example: Multicoloured circle

```python
from graphics import *
import random
import math

def r(win, n):
    p1 = Point(250, 250)
    radius = 250
    win.getMouse()
    for theta in range(int(divmod(360,n)[0])):
        for i in range(n):
            ntheta = theta + (i*(360/n))
            p2 = Point(250+(radius * math.cos(math.radians(ntheta))),250+(radius * math.sin(math.radians(ntheta))))
            lineA = Line(p1, p2)
            lineA.setOutline('#%06X' % random.randint(0, 0xFFFFFF))
            lineA.draw(win)
    win.getMouse()

def main():
    win = GraphWin('r', 500,500)
    r(win,4)

if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
