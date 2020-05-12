---
title: python script flowers (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'flowers'

Functions in program: 
* `def leafLeft():`
* `def leafRight():`
* `def stem2():`
* `def flower2():`
* `def stem():`
* `def flower():`
* `def rhombus():`
* `def circleUp2():`
* `def circleDown():`
* `def circleUp():`

Modules used in program: 
* `import time`
* `import random`
* `import turtle`

## python flowers

Python example: flowers

```python
import turtle
import random
import time


t = turtle.Turtle()
turtle.bgcolor("black")
t.speed(999)

red = 255, 0, 0
salmon = 250, 128, 114
orange = 255, 165, 0
yellow = 255, 255, 0
cornflowerBlue = 100, 149, 237
black = 0,0,0
green = 152, 251, 152
purple = 153, 50, 204
white = 255, 255, 255
navy = 0, 0, 128

turtle.colormode(255)
colors = [red, salmon, orange, yellow, cornflowerBlue]
colors2 = [purple, white, navy]

def circleUp():
	for i in range(6):
		t.circle(i*3)
		t.forward(10)

def circleDown():
	for i in range(6):
		t.circle(i*-3)
		t.backward(10)

def circleUp2():
	for i in range(6):
		t.circle(i*2)
		t.forward(5)

def rhombus():
	for i in range (2):
		t.forward(30)
		t.right(45)
		t.forward(30)
		t.right(135)

def flower():
	for i in range(6):
		circleUp()
		t.right(30)
		circleDown()
		t.right(30)

def stem():
	t.setheading(0)
	t.left(90)
	for i in range(30):
		t.forward(random.randint(5,7))
		t.right(.2)

def flower2():
	for i in range(36):
		rhombus()
		t.right(10)

def stem2():
	t.setheading(0)
	t.left(90)
	for i in range(30):
		t.forward(random.randint(7,9))
		t.left(.5)

def leafRight():
	t.penup()
	t.pencolor(green)
	t.setheading(0)
	t.goto(random.randint(-600,600), random.randint(-300,50))
	t.pendown()
	t.left(80)
	for i in range(4):
		circleUp2()
		t.right(15)

def leafLeft():
	t.penup()
	t.pencolor(green)
	t.setheading(0)
	t.goto(random.randint(-600,600), random.randint(-300,50))
	t.pendown()
	t.left(100)
	for i in range(4):
		circleUp2()
		t.left(15)

#leaves---------
for i in range (20):
	leafLeft()
	leafRight()

#smaller flowers------
for i in colors:
	t.setheading(0)
	t.color(i)
	t.penup()
	t.goto(random.randint(-600,600), random.randint(-300,50))
	t.pendown()

	for i in range(4):
		stem()
		flower()
		t.penup()
		t.goto(random.randint(-600,600), random.randint(-300,50))
		t.pendown()

#larger pointier flowers----
for i in colors2:
	t.setheading(0)
	t.color(i)
	t.penup()
	t.goto(random.randint(-600,600), random.randint(-300,50))
	t.pendown()

	for i in range(4):
		stem2()
		flower2()
		t.penup()
		t.goto(random.randint(-700,700), random.randint(-300,0))
		t.pendown()

time.sleep(10)


		






```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
