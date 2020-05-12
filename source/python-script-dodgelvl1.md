---
title: python script dodgelvl1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dodgelvl1'

Functions in program: 
* `def comp():`
* `def collide1():`
* `def collide():`
* `def right():`
* `def left():`
* `def up():`

Modules used in program: 
* `import random`
* `import time`
* `import turtle`

## python dodgelvl1

Python mysql example: dodgelvl1

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
enterdoor.goto(480,-260)
enterdoor.showturtle()

# score card
sc = turtle.Turtle()
sc.hideturtle()
sc.color('white')
sc.penup()
sc.goto(0,250)
sc.pensize(10)
sc.write('LEVEL : 1' , align = 'center' , font = ('courier' , 24 , 'normal'))

#protaganist

char = turtle.Turtle()
char.speed(0)
char.lt(90)
char.hideturtle()
char.color('red')
char.shape('triangle')
char.shapesize(1,1)
char.penup()
char.goto(450,-280)
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

# exit door
exitdoor = turtle.Turtle()
exitdoor.hideturtle()
exitdoor.color('white')
exitdoor.shape('square')
exitdoor.shapesize(3,2)
exitdoor.penup()
exitdoor.goto(485,265)
exitdoor.showturtle()

#--------------------------------------------    LOGIC    -------------------------------------------------------------------

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
        
def comp():
    if char.xcor() == exitdoor.xcor() and char.ycor() == exitdoor.ycor() or char.xcor() >= exitdoor.xcor() - 20 and char.xcor() <= exitdoor.xcor() + 20 and char.ycor() <= exitdoor.ycor() + 20 and char.ycor() >= exitdoor.ycor() - 20:
        sc.undo()
        sc.write('CLEARED!' , align = 'center' , font = ('courier' , 24 , 'normal'))
        time.sleep(3)
        sc.undo()
        char.hideturtle()
        gun.hideturtle()
        gun1.hideturtle()
        enterdoor.hideturtle()
        exitdoor.hideturtle()
        import Dodge2lvl2
                   
# bindings
win.listen()
win.onkeypress(up , 'w')
win.onkeypress(left , 'a')
win.onkeypress(right , 'd')

o = True
while o:
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

turtle.update()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
