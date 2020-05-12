---
title: python script recursive art advanced (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'recursive art advanced'

Functions in program: 
* `def draw_recursively(top_left, length):`
* `def draw_lines(top_left, length):`

Modules used in program: 
* `import random`
* `import math`
* `import sys`

## python recursive art advanced

Python mysql example: recursive art advanced

```python
import sys
sys.path.append('./MAS-1819/T1')
from grlib import graphics as gr
import math
import random

window_length = 800
outline_width = 1
black_color   = gr.color_rgb(11, 11, 11)
min_length    = 5 # 2, 5, 10 # should be positive over 1

win = gr.GraphWin('Recursive Art', window_length, window_length)
win.setBackground(black_color)

def draw_lines(top_left, length):

    length = int(length)

    number_of_points = random.randrange(5, 8)     
    
    points = [gr.Point(top_left.getX() + random.randrange(0, length),
                      top_left.getY() + random.randrange(0, length)) for i in range(number_of_points)]

    polygon = gr.Polygon(points)
    c = random.randrange(20, 90)
    color = gr.color_rgb(c, c, c)
    polygon.setOutline(color)
    polygon.setFill(color if random.random() < 0.2 else black_color)
    polygon.setWidth(1)
    polygon.draw(win)

def draw_recursively(top_left, length):
    
    if length <= min_length:
        return
    
    new_length = length * 0.5
    
    top_left_list = [
        top_left,
        gr.Point(top_left.getX() + new_length, top_left.getY()),
        gr.Point(top_left.getX(), top_left.getY() + new_length),
        gr.Point(top_left.getX() + new_length, top_left.getY() + new_length)
    ]
    
    drawing_index = random.randint(0, 3)

    drawing_top_left = top_left_list[drawing_index]

    draw_lines(drawing_top_left, new_length)
    
    top_left_list.pop(drawing_index)
    
    for top_left in top_left_list:
        draw_recursively(top_left, new_length)

length = window_length * 0.5
draw_recursively(gr.Point(0, 0), length)
draw_recursively(gr.Point(window_length * 0.5, 0), length)
draw_recursively(gr.Point(0, window_length * 0.5), length)
draw_recursively(gr.Point(window_length * 0.5, window_length * 0.5), length)

win.getMouse()
win.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
