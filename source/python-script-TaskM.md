---
title: python script TaskM (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'TaskM'


Modules used in program: 
* `import random`

## python TaskM

Python mysql example: TaskM

```python
import random

class Task:
  def __init__(self, time):
    self.timestamp = time 
    self.pages = random.randrange(1,21)
  
  def getStamp(self):
    return self.timestamp
  
  def getPages(self):
    return self.pages
  
  def waitTime(self, currenttime):
    return currenttime - self.timestamp

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
