---
title: python script class demo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'class demo'


Modules used in program: 
* `import random `

## python class demo

Python example: class demo

```python
#Import Random Library 
import random 
#Class Definition 
class Ball: 
  ''' A simple ball class to demonstrate OOP''' 
 
  #Constructor Function 
  def __init__(self, brand, age, color): 
    self.brand = brand 
    self.age = age 
    self.color = color 
    #Game for which ball is required and its speed in miles/hour 
    self.game = "Football" 
    self.speed = 0 
 
  #Method to kick the ball 
  def kick(self): 
    self.speed = random.randint(5,50) 
    print("Ball ",self.brand," has been kicked. Its new speed is ", self.speed, " miles/hour") 
 
  def stop(self): 
    if(self.speed == 0): 
      print("The ",self.brand," ball is already stopped") 
    else: 
      self.speed = 0 
      print(self.brand," Ball successfully stopped")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
