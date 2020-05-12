---
title: python script perceptron%2520learning%2520orGate%2520without%2520given%2520thetha (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'perceptron%2520learning%2520orGate%2520without%2520given%2520thetha'

Functions in program: 
* `def orGate():`

Modules used in program: 
* `import random`

## python perceptron%2520learning%2520orGate%2520without%2520given%2520thetha

Python mysql example: perceptron%2520learning%2520orGate%2520without%2520given%2520thetha

```python
import random
def orGate():
    # Or gate Learning
    weight1=round(random.uniform(-0.5,0.5), 1)    # to round the out to 1 decimal point
    weight2=round(random.uniform(-0.5,0.5), 1)  # to round the out to 1 decimal point
    print("Weighted intialization",weight1,weight2)
    weighto=round(random.uniform(-0.5,0.5), 1)  # to round the out to 1 decimal point
    xo=-1
    alpha=0.1
    flage=True     # flage will be false when convergence reaches
    output=1
    orGate=((0,0,0),(0,1,1),(1,0,1),(1,1,1))
    while(flage==True):
        flage=False
        for examp in orGate:
            value=(examp[0]*weight1)+(examp[1]*weight2)
            thetha=weighto*xo
            if(value+thetha>=0):      #if perceptoron excited as we know sum(wixi)>=thetha
                output=1    
            else:
                output=0
            if((output-examp[2])!=0):
                weight1=round(weight1+(alpha*(examp[2]-output)*examp[0]),1)   # to round the out to 1 decimal point
                weight2=round(weight2+(alpha*(examp[2]-output)*examp[1]),1)   # to round the out to 1 decimal point
                weighto=round(weighto+(alpha*(examp[2]-output)*xo),1)   # to round the out to 1 decimal point
                flage=True
    return (weight1,weight2,weighto)
weight1,weight2,weighto=orGate()
print(weight1,weight2,weighto)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
