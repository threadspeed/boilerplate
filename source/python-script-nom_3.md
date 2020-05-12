---
title: python script nom 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nom 3'

Functions in program: 
* `def main() :`
* `def ThirdFunc(p, N) :`
* `def SecondFunc(p, N) :`
* `def FirstFunc(p, N) :`
* `def Cc(m, N) :`
* `def BuildGraph(name, dataX, dataY) :`

Modules used in program: 
* `import matplotlib.pyplot as plt`

## python nom 3

Python mysql example: nom 3

```python
# -*- coding: utf-8 -*-


from math import *
import matplotlib.pyplot as plt


def BuildGraph(name, dataX, dataY) :
    graph = plt.figure()
    f = graph.add_subplot(111)
    f.plot(dataX, dataY)
    f.grid(True)
    f.set_xlabel("n")
    f.set_ylabel("p_n")
    f.set_title(name)
    plt.savefig(name + ".png")
    plt.show()
    
    
def Cc(m, N) :
    return factorial(N)/(factorial(N-m)*factorial(m))
    
    
def FirstFunc(p, N) :
    arr_pn = []
    arr_n = []
    
    for n in range(0, N+1) :
        pn = Cc(n, N) * (p**n) * ((1-p)**(N-n))
        arr_pn.append(pn)
        arr_n.append(n)
        
    BuildGraph("FirstFunc", arr_n, arr_pn)
    
    
def SecondFunc(p, N) :
    arr_pn = []
    arr_n = []
    
    for n in range(0, N+1) :
        pn = (((N*p)**n) / factorial(n)) * exp(-N*p)
        arr_pn.append(pn)
        arr_n.append(n)
        
    BuildGraph("SecondFunc", arr_n, arr_pn)
    

def ThirdFunc(p, N) :
    arr_pn = []
    arr_n = []
    
    sigma_sqr = p * (1 - p)
    dxn = 1/sqrt(N)
    for n in range(0, N+1) :
        xn = (n - N*p)/sqrt(N)
        pn = (1 / sqrt(2*pi*sigma_sqr)) * exp(-xn**2/(2*sigma_sqr)) * dxn
        arr_pn.append(pn)
        arr_n.append(n)
        
    BuildGraph("ThirdFunc", arr_n, arr_pn)


def main() :
    p = float(input("p: ")) ## p = 0.5
    N = int(input("N: ")) ## N = 50
    
    FirstFunc(p, N)
    SecondFunc(p, N)
    ThirdFunc(p, N)
    

if __name__ == "__main__" :
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
