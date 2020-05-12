---
title: python script dodgelvl7 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dodgelvl7'

Functions in program: 
* `def barochar1():`
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

## python dodgelvl7

Python mysql example: dodgelvl7

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
enterdoor.goto(-480,0)
enterdoor.showturtle()

# score card
sc = turtle.Turtle()
sc.hideturtle()
sc.color('white')
sc.penup()
sc.goto(0,250)
sc.pensize(10)
sc.write('LEVEL : 7 ' , align = 'center' , font = ('courier' , 24 , 'normal'))

#protaganist

char = turtle.Turtle()
char.speed(0)
char.hideturtle()
char.lt(180)
char.color('red')
char.shape('triangle')
char.shapesize(1,1)
char.penup()
char.goto(-480,0)
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
gun.goto(500,200)
gun.showturtle()

# bullet
blt = turtle.Turtle()
blt.hideturtle()
gun.lt(180)
blt.lt(180)
blt.color('orange')
blt.shape('circle')
blt.shapesize(1)
blt.speed(5)
blt.penup()
blt.goto(500,200)

# ball shooter 2
gun1 = turtle.Turtle()
gun1.speed(15)
gun1.hideturtle()
gun1.lt(180)
gun1.color('cyan')
gun1.shape('triangle')
gun1.shapesize(2)
gun1.penup()
gun1.goto(500,-200)
gun1.showturtle()

# bullet 
blt1 = turtle.Turtle()
blt1.hideturtle()
blt1.lt(180)
blt1.color('orange')
blt1.shape('circle')
blt1.shapesize(1)
blt1.speed(5)
blt1.penup()
blt1.goto(480,-200)

#gun 3
gun3 = turtle.Turtle()
gun3.speed(15)
gun3.hideturtle()
gun3.lt(180)
gun3.color('cyan')
gun3.shape('triangle')
gun3.shapesize(2)
gun3.penup()
gun3.goto(500,280)
gun3.showturtle()

blt3 = turtle.Turtle()
blt3.hideturtle()
blt3.lt(180)
blt3.color('orange')
blt3.shape('circle')
blt3.shapesize(1)
blt3.speed(5)
blt3.penup()
blt3.goto(500,280)

# gun 4
gun4 = turtle.Turtle()
gun4.speed(15)

gun4.hideturtle()
gun4.lt(180)
gun4.color('cyan')
gun4.shape('triangle')
gun4.shapesize(2)
gun4.penup()
gun4.goto(500,-280)
gun4.showturtle()

# bullet
blt4 = turtle.Turtle()
blt4.hideturtle()
blt4.lt(180)
blt4.color('orange')
blt4.shape('circle')
blt4.shapesize(1)
blt4.speed(5)
blt4.penup()
blt4.goto(500,-280)


# barrier 2
bar2 = turtle.Turtle()
bar2.hideturtle()
bar2.color('dark blue')
bar2.shape('square')
bar2.shapesize(19,2)
bar2.speed(0)
bar2.penup()
bar2.goto(0,0)
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
        import Dodge2lvl1
        
def barochar1():
    if bar2.xcor() == char.xcor() and bar2.ycor() == char.ycor() or bar2.xcor() > char.xcor() - 40 and bar2.xcor() < char.xcor() +40 and bar2.ycor() < char.ycor() + 180 and bar2.ycor() > char.ycor() - 180:
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
        
        barochar1()
    
    for i in range(50):
        
        barochar1()
        blt.fd(20)
        barochar1()
        
        collide()
    for i in range(50):
        
        barochar1()
        blt.backward(20)
        barochar1()
        
        collide()
    for i in range(1):
        blt.hideturtle()
    comp()
    barochar1()
    # gun 2 shoot
    for i in range(1):
        
        barochar1()
        blt1.showturtle()
        barochar1()
    for i in range(50):
        barochar1()
        
        blt1.fd(20)
        barochar1()
        collide1()
    for i in range(20):
        
        blt1.backward(50)
        
        collide1()
    for i in range(1):
        blt1.hideturtle()
    comp()
    barochar1()
    # gun 3 shoot
    for i in range(1):
        blt3.showturtle()
    
    for i in range(50):
        #barochar()
        barochar1()
        blt3.fd(20)
        #barochar()
        barochar1()
        collide2()
    for i in range(50):
        #barochar()
        barochar1()
        blt3.backward(20)
        #barochar()
        barochar1()
        collide2()
    for i in range(1):
        blt3.hideturtle()
    #barochar()
    comp()
    barochar1()
    # gun 4 shoot
    for i in range(1):
        blt4.showturtle()
    
    for i in range(50):
        #barochar()
        barochar1()
        blt4.fd(20)
        #barochar()
        barochar1()
        collide4()
    for i in range(50):
        #barochar()
        barochar1()
        blt4.backward(20)
        #barochar()
        barochar1()
        collide4()
    for i in range(1):
        #barochar()
        blt4.hideturtle()
    comp()
   
turtle.update()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
