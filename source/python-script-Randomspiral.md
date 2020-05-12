---
title: python script Randomspiral (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Randomspiral'

Functions in program: 
* `def Spiralrandom():`

Modules used in program: 
* `import random`
* `import turtle`

## python Randomspiral

Python example: Randomspiral

```python
import turtle
import random
t = turtle.Pen()
xa=0
ya=0
size=random.randint(10,40)

t.speed(9999999999999999)
colors=["red", "orange", "yellow", "green", "blue", "purple", "brown", "pink"]

def Spiralrandom():
    turtle.bgcolor("black")
    size=random.randint(10,40)
    xa=random.randint(-turtle.window_width()/2,turtle.window_width()/2)
    ya=random.randint(-turtle.window_height()/2,turtle.window_height()/2)
    t.pencolor(random.choice((colors)))
    t.penup()
    t.setpos(xa,ya)
    t.pendown()
    for y in range(size):
     t.forward(y)
     t.right(91)
     
for n in range(50):
    Spiralrandom()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
