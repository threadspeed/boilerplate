---
title: python script rhinoprocessing (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rhinoprocessing'


Modules used in program: 
* `import time`
* `import rhinoscriptsyntax as rs`
* `import scriptcontext`

## python rhinoprocessing

Python mysql example: rhinoprocessing

```python
import scriptcontext
import rhinoscriptsyntax as rs
import time

class Rhino_Processing():
    
    def __init__(self):
        self.refresh = True
        self.start_time = time.time()
        self.frame_no = 0
        
        self.loop()
        
    
    def loop(self):
        print('-- process start. (ESC to end) --')

        self.setup()
        self.run()
    
    def setup(self):
        #####
        self.point = rs.AddPoint([100,0,0])
        
    def draw(self):
        #####
        rs.RotateObject(self.point,[0,0,0],1)
        
    def enable_refresh(self,_bool=True):
        self.refresh = _bool
        
    def fps(self):
        delta_time = time.time() - self.start_time
        if delta_time > 0.0:
            frame_rate = self.frame_no / delta_time
        else:
            frame_rate = 0
        return frame_rate
        
    def run(self):
        while True:
            
            if self.refresh:
                scriptcontext.doc.Views.Redraw()
            
            rs.EnableRedraw(False)
            self.draw()
            rs.EnableRedraw()
            
            if scriptcontext.escape_test(False):
                print('-- process end. fps: '+ str(self.fps())+' --')
                break
            
            self.frame_no += 1
                

if __name__ == "__main__":
    loop = Rhino_Processing()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
