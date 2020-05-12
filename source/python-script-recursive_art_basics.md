---
title: python script recursive art basics (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'recursive art basics'

Functions in program: 
* `def draw_shape(top_left, length):`

Modules used in program: 
* `import random`
* `import math`
* `import sys`

## python recursive art basics

Python example: recursive art basics

```python
window_length = 800
import sys
sys.path.append('./MAS-1819/T1')
from grlib import graphics as gr
import math
import random

outline_width = 1

win = gr.GraphWin('Recursive Art', window_length, window_length)

black_color = gr.color_rgb(11, 11, 11)
white_color = gr.color_rgb(100, 100, 100)

def draw_shape(top_left, length):
    
    if length <= window_length * 0.01:
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

    bottom_right = gr.Point(drawing_top_left.getX() + new_length,
                                drawing_top_left.getY() + new_length)

    rect = gr.Rectangle(drawing_top_left, bottom_right)
    c = black_color if random.random() > 0.1 else white_color
    rect.setFill(c)
    rect.setOutline(white_color)
    rect.setWidth(1)
    rect.draw(win)
    
    if random.random() < 0.5:
        
        center = gr.Point(drawing_top_left.getX() + new_length * 0.5,
                          drawing_top_left.getY() + new_length * 0.5)
        circle = gr.Circle(center, new_length * 0.5)

        c = black_color if random.random() > 0.1 else white_color
        circle.setFill(c)

        circle.setOutline(white_color)
        circle.setWidth(1)
        circle.draw(win)
    
    top_left_list.pop(drawing_index)
    
    for top_left in top_left_list:
        draw_shape(top_left, new_length)

win.setBackground(black_color)

length = window_length * 0.5
draw_shape(gr.Point(0, 0), length)
draw_shape(gr.Point(window_length * 0.5, 0), length)
draw_shape(gr.Point(0, window_length * 0.5), length)
draw_shape(gr.Point(window_length * 0.5, window_length * 0.5), length)

win.getMouse()
win.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
