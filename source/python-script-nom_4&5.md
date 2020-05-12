---
title: python script nom 4&5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nom 4&5'

Functions in program: 
* `def main() :`
* `def Nomber5(a, b) :`
* `def Nomber4(a, b) :`
* `def BuildGrpah(hist_data, graph_data) :`

Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`

## python nom 4&5

Python mysql example: nom 4&5

```python
# -*- coding: utf-8 -*-


from math import *
import matplotlib.pyplot as plt
from random import random
from scipy.special import gamma, hyp2f1
import numpy as np


def BuildGrpah(hist_data, graph_data) :
    bins = np.linspace(0, 2.2, 50)
    plt.hist(hist_data, bins, density=True)
    plt.plot(graph_data[0], graph_data[1])
    plt.savefig("keks.png")
    plt.show()
    

def Nomber4(a, b) :
    
    def Distribution(a, b) :
        return random()**a + random()**b
    
    
    data = []
    for i in range(100000) :
        g = Distribution(a, b)
        data.append(g)
        
    return data
    
    
def Nomber5(a, b) :
    
    def P1(x) :
        return (x**(1/a + 1/b - 1)) * (gamma(1+1/a)*gamma(1+1/b) / gamma(1/a+1/b))
    
    
    def P2(x) :
        A = hyp2f1(1/a, 1-1/b, 1/a+1, 1/x) - (x-1)**(1/a)*hyp2f1(1/a, 1-1/b, 1/a+1, 1-1/x)
        return A * x**(1/b-1)/b
 
 
    def Distribution(x) :
        if -0 <= x <= 1 :
            return P1(x)
        return P2(x)
    
    
    dataX, dataY = [], []
    x = 0
    while x < 2 :
        p = Distribution(x)
        dataX.append(x)
        dataY.append(p)
        x += 0.001

    return [dataX, dataY]
    
    
def main() :
    a = float(input("a: ")) #a = 0.5
    b = float(input("b: ")) #b = 0.1
    hist_data = Nomber4(a, b)
    graph_data = Nomber5(a, b)
    BuildGrpah(hist_data, graph_data)
    
    
if __name__ == "__main__" :
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
