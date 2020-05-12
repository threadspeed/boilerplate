---
title: python script lesson 1 Class (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lesson 1 Class'


Modules used in program: 
* `import turtle`

## python lesson 1 Class

Python example: lesson 1 Class

```python
import turtle
from time import *

class Things:
    pass

class Inanimate (Things):
    pass

class Animate (Things):
    pass

class Sidewalks (Inanimate):
    pass

class Animals (Animate):
    def breathe(self):
        print('Дышит полной грудью')
    def move(self):
        print('Шевелит конечностями')
    def eat_food(self):
        print('кушает')

class Mammals (Animals):
    def feed_young_with_milk(self):
        print('Кормит детенышей молоком')


class Giraffes (Mammals):
    def __init__(self, spots):
        self.giraffe_spots = spots
    def eat_leaves_from_trees(self):
        print('ест листья с верхушек деревьев')
    def find_food(self):
        self.move()
        print('Я нашел где похавать')
        self.eat_food()
    def dance_a_jig(self):
        self.move()
        self.move()
        self.move()
        self.move()




ferdinant = Giraffes(100)
harold = Giraffes(100)
reginald = Giraffes(100)
reginald.dance_a_jig()
ferdinant.move()
harold.eat_food()
harold.move()
harold.eat_leaves_from_trees()
reginald.eat_food()

ozwald = Giraffes(100)
gertrude = Giraffes(150)

print(ozwald.giraffe_spots)
print(harold.giraffe_spots)
avery = turtle.Pen()
kate = turtle.Pen()
jacob = turtle.Pen()

avery.forward(100)
avery.right(90)
avery.forward(100)


kate.left(120)
kate.forward(100)

jacob.left(180)
jacob.forward(100)

sleep(10)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
