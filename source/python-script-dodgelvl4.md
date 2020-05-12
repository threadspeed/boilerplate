---
title: python script dodgelvl4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dodgelvl4'

Functions in program: 
* `def comp():`
* `def collide4():`
* `def collide2():`
* `def collide1():`
* `def collide():`
* `def right():`
* `def left():`
* `def up():`

Modules used in program: 
* `import random`
* `import time`
* `import turtle`

## python dodgelvl4

Python mysql example: dodgelvl4

```python
import turtle
import time
import random

#--------------------------------------------    APPERANCE    --------------------------------------------------------------

# screen setup
win = turtle.Screen()
win.bgcolor('black')
win.title('Dodge 2')
win.setup(1200,600)

# starting door
enterdoor = turtle.Turtle()
enterdoor.speed(15)
enterdoor.hideturtle()
enterdoor.color('white')
enterdoor.shape('square')
enterdoor.shapesize(3,2)
enterdoor.penup()
enterdoor.goto(480 , 260)
enterdoor.showturtle()

# score card
sc = turtle.Turtle()
sc.hideturtle()
sc.color('white')
sc.penup()
sc.goto(0,250)
sc.pensize(10)
sc.write('LEVEL : 4' , align = 'center' , font = ('courier' , 24 , 'normal'))

#protaganist

char = turtle.Turtle()
char.speed(0)
char.lt(180)
char.hideturtle()
char.color('red')
char.shape('triangle')
char.shapesize(1,1)
char.penup()
char.goto(480 , 260)
char.speed(0)
char.showturtle()

# ball shooter 1
gun = turtle.Turtle()
gun.speed(15)
gun.hideturtle()
gun.color('cyan')
gun.shape('triangle')
gun.shapesize(2)
gun.penup()
gun.goto(-500,0)
gun.showturtle()

# bullet
blt = turtle.Turtle()
blt.hideturtle()
blt.color('orange')
blt.shape('circle')
blt.shapesize(1)
blt.speed(5)
blt.penup()
blt.goto(-500,0)

# ball shooter 2
gun1 = turtle.Turtle()
gun1.speed(15)
gun1.rt(90)
gun1.hideturtle()
gun1.color('cyan')
gun1.shape('triangle')
gun1.shapesize(2)
gun1.penup()
gun1.goto(0,280)
gun1.showturtle()

# bullet 
blt1 = turtle.Turtle()
blt1.hideturtle()
blt1.rt(90)
blt1.color('orange')
blt1.shape('circle')
blt1.shapesize(1)
blt1.speed(5)
blt1.penup()
blt1.goto(0,280)

# gun 3
gun3 = turtle.Turtle()
gun3.speed(15)
gun3.hideturtle()
gun3.lt(90)
gun3.color('cyan')
gun3.shape('triangle')
gun3.shapesize(2)
gun3.penup()
gun3.goto(-250,-280)
gun3.showturtle()

blt3 = turtle.Turtle()
blt3.hideturtle()
blt3.lt(90)
blt3.color('orange')
blt3.shape('circle')
blt3.shapesize(1)
blt3.speed(5)
blt3.penup()
blt3.goto(-250,-280)

# gun 4
gun4 = turtle.Turtle()
gun4.speed(15)
gun4.lt(90)
gun4.hideturtle()
gun4.color('cyan')
gun4.shape('triangle')
gun4.shapesize(2)
gun4.penup()
gun4.goto(250,-280)
gun4.showturtle()

# bullet
blt4 = turtle.Turtle()
blt4.hideturtle()
blt4.lt(90)
blt4.color('orange')
blt4.shape('circle')
blt4.shapesize(1)
blt4.speed(5)
blt4.penup()
blt4.goto(250,-280)

# exit door
exitdoor = turtle.Turtle()
exitdoor.hideturtle()
exitdoor.color('white')
exitdoor.shape('square')
exitdoor.shapesize(3,2)
exitdoor.penup()
exitdoor.goto(-480,-260)
exitdoor.showturtle()

 # ------- LOGIC- --------

def up():
    char.fd(20)
def left():
    char.lt(90)
def right():
    char.rt(90)
def collide():
    if blt.xcor() == char.xcor() and blt.ycor() == char.ycor() or blt.xcor() > char.xcor()-20 and blt.xcor() < char.xcor() +20 and (blt.ycor() < char.ycor() + 20) and blt.ycor() > char.ycor() - 20:
        sc.undo()
        sc.write('HARD LUCK!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        turtle.bye()
def collide1():
    if blt1.xcor() == char.xcor() and blt1.ycor() == char.ycor() or blt1.xcor() > char.xcor()-20 and blt1.xcor() < char.xcor() +20 and (blt1.ycor() < char.ycor() + 20) and blt1.ycor() > char.ycor() - 20:
        sc.undo()
        sc.write('HARD LUCK!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        turtle.bye()
def collide2():
    if blt3.xcor() == char.xcor() and blt3.ycor() == char.ycor() or blt3.xcor() > char.xcor()-20 and blt3.xcor() < char.xcor() +20 and (blt3.ycor() < char.ycor() + 20) and blt3.ycor() > char.ycor() - 20:
        sc.undo()
        sc.write('HARD LUCK!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        turtle.bye()
def collide4():
    if blt4.xcor() == char.xcor() and blt4.ycor() == char.ycor() or blt4.xcor() > char.xcor()-20 and blt4.xcor() < char.xcor() +20 and (blt4.ycor() < char.ycor() + 20) and blt4.ycor() > char.ycor() - 20:
        sc.undo()
        sc.write('HARD LUCK!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        turtle.bye()
        
def comp():
    if char.xcor() == exitdoor.xcor() and char.ycor() == exitdoor.ycor() or char.xcor() >= exitdoor.xcor() - 20 and char.xcor() <= exitdoor.xcor() + 20 and char.ycor() <= exitdoor.ycor() + 20 and char.ycor() >= exitdoor.ycor() - 20:
        sc.undo()
        sc.write('CLEARED!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        sc.undo()
        char.hideturtle()
        gun.hideturtle()
        gun1.hideturtle()
        gun3.hideturtle()
        gun4.hideturtle()
        enterdoor.hideturtle()
        exitdoor.hideturtle()
        import Dodge2lvl5
                   
# bindings
win.listen()
win.onkeypress(up , 'w')
win.onkeypress(left , 'a')
win.onkeypress(right , 'd')

o = True
while o:
    # gun 1 shoot
    for i in range(1):
        blt.showturtle()
    
    for i in range(100):
        blt.fd(10)
        collide()
    for i in range(100):
        blt.backward(10)
        collide()
    for i in range(1):
        blt.hideturtle()
    comp()
    # gun 2 shoot
    for i in range(1):
        blt1.showturtle()
    for i in range(56):
        blt1.fd(10)
        collide1()
    for i in range(56):
        blt1.backward(10)
        collide1()
    for i in range(1):
        blt1.hideturtle()
    comp()
    # gun 3 shoot
    for i in range(1):
        blt3.showturtle()
    
    for i in range(56):
        blt3.fd(10)
        collide2()
    for i in range(56):
        blt3.backward(10)
        collide2()
    for i in range(1):
        blt3.hideturtle()
    comp()
    # gun 4 shoot
    for i in range(1):
        blt4.showturtle()
    
    for i in range(56):
        blt4.fd(10)
        collide4()
    for i in range(56):
        blt4.backward(10)
        collide4()
    for i in range(1):
        blt4.hideturtle()
    comp()

turtle.update()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
