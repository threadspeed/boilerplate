---
title: python script dodgelvl2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dodgelvl2'

Functions in program: 
* `def comp():`
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

## python dodgelvl2

Python example: dodgelvl2

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
enterdoor.goto(485 , 265)
enterdoor.showturtle()

# score card
sc = turtle.Turtle()
sc.hideturtle()
sc.color('white')
sc.penup()
sc.goto(0,250)
sc.pensize(10)
sc.write('LEVEL : 2' , align = 'center' , font = ('courier' , 24 , 'normal'))

#protaganist

char = turtle.Turtle()
char.speed(0)
char.lt(270)
char.hideturtle()
char.color('red')
char.shape('triangle')
char.shapesize(1,1)
char.penup()
char.goto(485,265)
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
gun.goto(-500,-170)
gun.showturtle()

# bullet
blt = turtle.Turtle()
blt.hideturtle()
blt.color('orange')
blt.shape('circle')
blt.shapesize(1)
blt.speed(5)
blt.penup()
blt.goto(-500,-170)

# ball shooter 2
gun1 = turtle.Turtle()
gun1.speed(15)
gun1.hideturtle()
gun1.color('cyan')
gun1.shape('triangle')
gun1.shapesize(2)
gun1.penup()
gun1.goto(-500,170)
gun1.showturtle()

# bullet 
blt1 = turtle.Turtle()
blt1.hideturtle()
blt1.color('orange')
blt1.shape('circle')
blt1.shapesize(1)
blt1.speed(5)
blt1.penup()
blt1.goto(-500,170)

# gun 3
gun3 = turtle.Turtle()
gun3.speed(15)
gun3.hideturtle()
gun3.lt(180)
gun3.color('cyan')
gun3.shape('triangle')
gun3.shapesize(2)
gun3.penup()
gun3.goto(500,0)
gun3.showturtle()

blt3 = turtle.Turtle()
blt3.hideturtle()
blt3.lt(180)
blt3.color('orange')
blt3.shape('circle')
blt3.shapesize(1)
blt3.speed(5)
blt3.penup()
blt3.goto(500,0)

# exit door
exitdoor = turtle.Turtle()
exitdoor.hideturtle()
exitdoor.color('white')
exitdoor.shape('square')
exitdoor.shapesize(3,2)
exitdoor.penup()
exitdoor.goto(480,-260)
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
        enterdoor.hideturtle()
        exitdoor.hideturtle()
        import Dodge2lvl3
                   
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
    for i in range(1):
        blt.speed(0)
        blt.hideturtle()
        blt.goto(-500,-170)
        blt.speed(5)
    comp()
    # gun 2 shoot
    for i in range(1):
        blt1.showturtle()
    for i in range(100):
        blt1.fd(10)
        collide1()
    for i in range(1):
        blt1.speed(0)
        blt1.hideturtle()
        blt1.goto(-500,170)
        blt1.speed(5)
    comp()
    # gun 3 shoot
    for i in range(1):
        blt3.showturtle()
    
    for i in range(100):
        blt3.fd(10)
        collide2()
    for i in range(1):
        blt3.speed(0)
        blt3.hideturtle()
        blt3.goto(500,0)
        blt3.speed(5)
    comp()

turtle.update()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
