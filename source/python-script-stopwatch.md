---
title: python script stopwatch (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'stopwatch'

Functions in program: 
* `def draw(canvas):`
* `def reset():`
* `def start():`
* `def format(t):`

Modules used in program: 
* `import simplegui`

## python stopwatch

Python mysql example: stopwatch

```python
# Mini Project 3 for An Introduction to Interactive Programming in Python
# template for "Stopwatch: The Game"
# url http://www.codeskulptor.org/#user6-9xfKUFzg7yNqyvg.py

import simplegui

# define global variables
i = 0
interval = 100

# define helper function format that converts integer
# counting tenths of seconds into formatted string A:BC.D
def format(t):
    a = int(t/60000)
    #print(a)
    b = int((t - a *60000)/1000)
    #print(b)
    d = int((t- a*60000 - 1000*b)/100)
    #print(d)
    return str(a)+':'+str(b)+'.'+str(d)
    
# define event handlers for buttons; "Start", "Stop", "Reset"
def start():
    global i
    global interval
    i += interval
    
def reset():
    global i
    i = 0

# define event handler for timer with 0.1 sec interval
def draw(canvas):
    canvas.draw_text(format(i), [100,100],36, 'Red')
    
    
# create frame
frame = simplegui.create_frame("Stop Watch", 300, 200)

# register event handlers
frame.set_draw_handler(draw)
timer = simplegui.create_timer(interval, start)
button1 = frame.add_button("Start", timer.start, 75)
button2 = frame.add_button("Stop", timer.stop, 75)
button3 = frame.add_button("Reset", reset, 75)

# start timer and frame
frame.start()
#timer.start()

# remember to review the grading rubric


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
