---
title: python script wumpus class (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wumpus class'


## python wumpus class

Python mysql example: wumpus class

```python
class rum(object):
    import random

    def __init__(self, rum, parts,y_pos,x_pos):
        self.rum = rum
        self.parts = parts
        self.y_pos = y_pos
        self.x_pos = x_pos



  

    def split(self,parts,rum):
        length = len(rum)
        maze =[ rum[i*length // parts: (i+1)*length // parts] for i in range(parts) ]
        return maze

    def allignement_check(self,y_pos,x_pos,maze):
        if y_pos < 0:
            y_pos = (len(maze))-1

        if y_pos >= len(maze):
            y_pos = 0

        if x_pos >= len(maze[y_pos]):
            x_pos = 0
        
        if x_pos < 0:
            x_pos = len(maze[y_pos])-1

        return y_pos,x_pos



            

        

  


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
