---
title: python script PrinterM (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PrinterM'


## python PrinterM

Python example: PrinterM

```python
class Printer:
  def __init__(self, ppm):
    self.pagerate = ppm
    self.currentTask = None
    self.timeRemaining = 0
  
  def tick(self):
    if self.currentTask != None:
      self.timeRemaining = self.timeRemaining - 1
      if self.timeRemaining <= 0:
        self.currentTask = None
  
  def busy(self):
    if self.currentTask != None:
      return True
    else:
      return False
  
  def startNext(self, newtask):
    self.currentTask = newtask
    self.timeRemaining = newtask.getPages() * 60/self.pagerate

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
