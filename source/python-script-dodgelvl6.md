---
title: python script dodgelvl6 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dodgelvl6'

Functions in program: 
* `def barochar1():`
* `def barochar():`
* `def comp():`
* `def collide5():`
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

## python dodgelvl6

Python mysql example: dodgelvl6

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
sc.write('LEVEL : 6 ' , align = 'center' , font = ('courier' , 24 , 'normal'))

#protaganist

char = turtle.Turtle()
char.speed(0)
char.lt(90)
char.hideturtle()
char.color('red')
char.shape('triangle')
char.shapesize(1,1)
char.penup()
char.goto(480 , -260)
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
gun1.hideturtle()
gun1.color('cyan')
gun1.shape('triangle')
gun1.shapesize(2)
gun1.penup()
gun1.goto(-500,-140)
gun1.showturtle()

# bullet 
blt1 = turtle.Turtle()
blt1.hideturtle()
blt1.color('orange')
blt1.shape('circle')
blt1.shapesize(1)
blt1.speed(5)
blt1.penup()
blt1.goto(-480,-140)

# gun 3
gun3 = turtle.Turtle()
gun3.speed(15)
gun3.hideturtle()
gun3.color('cyan')
gun3.shape('triangle')
gun3.shapesize(2)
gun3.penup()
gun3.goto(-500,140)
gun3.showturtle()

blt3 = turtle.Turtle()
blt3.hideturtle()
blt3.color('orange')
blt3.shape('circle')
blt3.shapesize(1)
blt3.speed(5)
blt3.penup()
blt3.goto(-480,140)

# gun 4
gun4 = turtle.Turtle()
gun4.speed(15)
gun4.lt(90)
gun4.hideturtle()
gun4.color('cyan')
gun4.shape('triangle')
gun4.shapesize(2)
gun4.penup()
gun4.goto(0,-280)
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
blt4.goto(0,-280)

# gun 5
gun5 = turtle.Turtle()
gun5.speed(15)
gun5.lt(90)
gun5.hideturtle()
gun5.color('cyan')
gun5.shape('triangle')
gun5.shapesize(2)
gun5.penup()
gun5.goto(250,-280)
gun5.showturtle()

# bullet
blt5 = turtle.Turtle()
blt5.hideturtle()
blt5.lt(90)
blt5.color('orange')
blt5.shape('circle')
blt5.shapesize(1)
blt5.speed(5)
blt5.penup()
blt5.goto(250,-280)

# barrier 1
bar = turtle.Turtle()
bar.hideturtle()
bar.color('dark blue')
bar.shape('square')
bar.shapesize(2,12)
bar.speed(0)
bar.penup()
bar.goto(405,-70)
bar.showturtle()

# barrier 2
bar2 = turtle.Turtle()
bar2.hideturtle()
bar2.color('dark blue')
bar2.shape('square')
bar2.shapesize(12,2)
bar2.speed(0)
bar2.penup()
bar2.goto(305,40)
bar2.showturtle()

# exit door
exitdoor = turtle.Turtle()
exitdoor.hideturtle()
exitdoor.color('white')
exitdoor.shape('square')
exitdoor.shapesize(3,2)
exitdoor.penup()
exitdoor.goto(480,0)
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

def collide5():
    if blt5.xcor() == char.xcor() and blt5.ycor() == char.ycor() or blt5.xcor() > char.xcor()-20 and blt5.xcor() < char.xcor() +20 and (blt5.ycor() < char.ycor() + 20) and blt5.ycor() > char.ycor() - 20:
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
        enterdoor.hideturtle()
        exitdoor.hideturtle()
        gun.hideturtle()
        gun1.hideturtle()
        gun3.hideturtle()
        gun4.hideturtle()
        gun5.hideturtle()
        bar.hideturtle()
        bar2.hideturtle()
        import Dodge2lvl7
def barochar():
    if bar.xcor() == char.xcor() and bar.ycor() == char.ycor() or bar.xcor() > char.xcor() - 80 and bar.xcor() < char.xcor() +80 and bar.ycor() < char.ycor() + 20 and bar.ycor() > char.ycor() - 20:
        char.setpos(char.xcor() , char.ycor()- 20)
def barochar1():
    if bar2.xcor() == char.xcor() and bar2.ycor() == char.ycor() or bar2.xcor() > char.xcor() - 20 and bar2.xcor() < char.xcor() +20 and bar2.ycor() < char.ycor() + 100 and bar2.ycor() > char.ycor() - 100:
        char.setpos(char.xcor() - 20 , char.ycor())
                   
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
        barochar()
        barochar1()
    
    for i in range(80):
        barochar()
        barochar1()
        blt.fd(10)
        barochar1()
        barochar()
        collide()
    for i in range(40):
        barochar()
        barochar1()
        blt.backward(20)
        barochar1()
        barochar()
        collide()
    for i in range(1):
        barochar()
        blt.hideturtle()
    comp()
    barochar1()
    # gun 2 shoot
    for i in range(1):
        barochar()
        barochar1()
        blt1.showturtle()
        barochar1()
    for i in range(100):
        barochar1()
        barochar()
        blt1.fd(10)
        barochar()
        barochar1()
        collide1()
    for i in range(50):
        barochar()
        blt1.backward(20)
        barochar()
        collide1()
    for i in range(1):
        blt1.hideturtle()
    comp()
    barochar1()
    # gun 3 shoot
    for i in range(1):
        blt3.showturtle()
    
    for i in range(100):
        barochar()
        barochar1()
        blt3.fd(10)
        barochar()
        barochar1()
        collide2()
    for i in range(50):
        barochar()
        barochar1()
        blt3.backward(20)
        barochar()
        barochar1()
        collide2()
    for i in range(1):
        blt3.hideturtle()
    barochar()
    comp()
    barochar1()
    # gun 4 shoot
    for i in range(1):
        blt4.showturtle()
    
    for i in range(56):
        barochar()
        barochar1()
        blt4.fd(10)
        barochar()
        barochar1()
        collide4()
    for i in range(28):
        barochar()
        barochar1()
        blt4.backward(20)
        barochar()
        barochar1()
        collide4()
    for i in range(1):
        barochar()
        blt4.hideturtle()
        barochar()
    barochar()
    comp()
    barochar()
    barochar1()

    # gun 5 shoot
    for i in range(1):
        blt5.showturtle()
    
    for i in range(56):
        barochar()
        barochar1()
        blt5.fd(10)
        barochar()
        barochar1()
        collide5()
    for i in range(28):
        barochar()
        barochar1()
        blt5.backward(20)
        barochar()
        barochar1()
        collide5()
    for i in range(1):
        barochar()
        barochar1()
        blt5.hideturtle()
        barochar()
    barochar()
    barochar1()
    comp()
    barochar()

turtle.update()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
