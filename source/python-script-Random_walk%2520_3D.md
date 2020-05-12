---
title: python script Random walk%2520 3D (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random walk%2520 3D'

Functions in program: 
* `def init() :`
* `def update(*args) :`
* `def RW( t, xc, yc, zc, xlm, ylm, zlm, a, mk, azmt):`

Modules used in program: 
* `import matplotlib.animation as animation`
* `import matplotlib.animation as animation`
* `import random`

## python Random walk%2520 3D

Python mysql example: Random walk%2520 3D

```python
import random
import matplotlib.animation as animation
from matplotlib import pyplot
from mpl_toolkits.mplot3d import Axes3D

pyplot.style.use("ggplot")

z = "wheat"import random
import matplotlib.animation as animation
from matplotlib import pyplot
from mpl_toolkits.mplot3d import Axes3D

pyplot.style.use("bmh") #ggplot


fig, g = pyplot.subplots(figsize=(6.4,4.8)) 
 
pyplot.subplots_adjust(top = 1.0, left = 0.00, right = 1.00,  bottom = 0.00)
pyplot.rcParams['axes.facecolor'] = "white"
pyplot.rcParams['savefig.facecolor'] = "whitesmoke"

def RW( t, xc, yc, zc, xlm, ylm, zlm, a, mk, azmt):
 
 ax = fig.gca(projection='3d')   
    
 if t == 1 : # full path   
    ax.plot(xc,yc,zc, linewidth = 0.9, marker = None, c = "red", alpha = a)
 
 if t == 2 : # last 5 steps   
    ax.plot(xc,yc,zc, linewidth = 0.9, marker = None, c = "maroon", alpha = a)   
 
 if t == 3 : 
    ax.scatter (xc, yc, zc, zdir="z", marker = mk, c="steelblue", alpha = a)
 
 
 ax.set_xlim(xlm) 
 ax.set_zlim(zlm)
 ax.set_ylim(ylm)
 
 ax.set_yticklabels([])
 ax.set_xticklabels([])
 ax.set_zticklabels([]) 
 
 ax.set_zticks([])
  
 ax.yaxis.line.set_color((1.0,1.0,1.0,0.0))
 ax.xaxis.line.set_color((1.0,1.0,1.0,0.0))
 ax.zaxis.line.set_color((1.0,1.0,1.0,0.0))

 ax.dist = 11
 ax.azim = azmt
 
 pyplot.show() 

 return


ctd = 0

## Random walk steps
sim = 200 # Number of steps

# Initial points
xc = [0] 
yc = [0] 
zc = [0] 

for n in range(sim) :

  c = random.choice([0,1,2,3,4,5])
  
  if c == 0 :
     xc.append(xc[-1]+1) # step x-right  
     yc.append(yc[-1])
     zc.append(zc[-1])
    
  if c == 1 :
     xc.append(xc[-1]-1) # step x-left 
     yc.append(yc[-1])  
     zc.append(zc[-1])
    
  if c == 2 :
     xc.append(xc[-1])   # step y-up 
     yc.append(yc[-1]+1)  
     zc.append(zc[-1])
    
  if c == 3 :
     xc.append(xc[-1])   # step y-down 
     yc.append(yc[-1]-1)   
     zc.append(zc[-1])
   
  if c == 4 :
     xc.append(xc[-1])   # step z-up 
     yc.append(yc[-1])  
     zc.append(zc[-1]+1)  
    
  if c == 5 :
     xc.append(xc[-1])   # step z-down 
     yc.append(yc[-1])  
     zc.append(zc[-1]-1)  
      
      
#Scaling axis:
 
xa = abs(min(xc))+1
xb = abs(max(xc))+1
ya = abs(min(yc))+1
yb = abs(max(yc))+1
za = abs(min(zc))+1
zb = abs(max(zc))+1

azmt = 0


xlm = (-xa,xb)
ylm = (-ya,yb)
zlm = (-za,zb)
 
def update(*args) :
  pyplot.clf()
  global xc,yc,zc,xlm,ylm,zlm,sim,ctd,azmt
  
  
  RW(1,xc[:ctd+1],yc[:ctd+1],zc[:ctd+1],xlm,ylm,zlm, 0.5, 0,azmt) 
  RW(3,xc[ctd],yc[ctd],zc[ctd],xlm,ylm,zlm, 0.9, "o",azmt)
  RW(3,xc[0],yc[0],zc[0],xlm,ylm,zlm, 0.9, "s",azmt) # Initial point
  
  if ctd > 5 : # trail of the last steps
     RW(2,xc[ctd-4:ctd+1],yc[ctd-4:ctd+1],zc[ctd-4:ctd+1],xlm,ylm,zlm, 0.5,0,azmt) 
  
  if ctd < sim :
     ctd +=1
  
  azmt += 360/sim  
    
  return ()
  

def init() :
       
    return()

anim = animation.FuncAnimation(fig, update, init_func=init, blit = True, frames=sim+45, repeat = False) 

                              
sf = "Random_W_3d.gif"      
Sname = "C:\\Users\\Rober\\Desktop\\_" + sf   # Saving path

anim.save(Sname, writer="imagemagick", fps=15)  


# You must have imagemagick installed in you computer :
# https://www.imagemagick.org/script/index.php


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
