---
title: python script analizator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'analizator'

Functions in program: 
* `def xi(ti,tau):`
* `def sizeOfParts(tparted):`
* `def getProb(ti,f):`
* `def partitioning(ti):`
* `def Lsum(xi):`
* `def getRes(filename):`

Modules used in program: 
* `import generator`

## python analizator

Python example: analizator

```python
# Лабораторна робота №1
# Комп'ютерне моделювання
# Вітьман
# Аналіз дифузійного монотонного розподілу


from random import random
from math import sqrt, exp, pi, log
import generator

# ксть розбиттів 
n=3

def getRes(filename):
    fin=open(filename,"r")
    s=fin.readlines()
    for i in range(len(s)):
        s[i]=float(s[i].replace("\n",""))
    return s

def Lsum(xi):
    S=0
    for x in xi:
        if x>0 :
            S+=log(x)
    return S


def partitioning(ti):

    ti.sort()
    

    l=ti[-1]-ti[0]
    dl=l/n
    lcarent=ti[0]+dl

    j=0
    tpart=[[]]
    for i in range(len(ti)):
        if (ti[i]>lcarent):
            j+=1
            lcarent+=dl
            tpart.append([])

        tpart[j].append(ti[i])


    return tpart

def getProb(ti,f):
    ti.sort()
    prob=[]

    l=ti[-1]-ti[0]
    dl=l/n
    lcarent=0.001

    for i in range(n-1):
        prob.append(generator.integral(f,lcarent,lcarent+dl))
        lcarent+=dl
    prob.append(generator.integral(f,lcarent,lcarent+dl*5))
    return prob

def sizeOfParts(tparted):
    sp=[]
    for i in range(len(tparted)):
        sp.append(len(tparted[i]))
    return sp

def xi(ti,tau):
    parts = partitioning(ti)
    m=sizeOfParts(parts)
    print(m)
    n=len(ti)
    parts.append([100])
    p=getProb(ti,generator.f(tau))
    print(p)
    x=0
    for i in range(len(m)):
        
        x+=((m[i]-n*p[i])**2) /(n*p[i])

       
    return x
    


if __name__ =="__main__":
    
    ltau=0.01
    dtau=0.01
    rtau=100.0
    lenTau=rtau-ltau
    ti=getRes("lab1.generated.txt")
    
    q=True
    while (q):
      # print((rtau-ltau)/lenTau*100)
        
        f=generator.f(rtau)
        right=[f(t) for t in ti]

        f=generator.f(ltau)
        left=[f(t) for t in ti]

        mtau=(ltau+rtau)/2.0
        f=generator.f(mtau)
        mid=[f(t) for t in ti]

        if (Lsum(left)<=Lsum(mid)):
            ltau+=dtau
        elif (Lsum(right)<=Lsum(mid)):
            rtau-=dtau
        else:
            ltau+=dtau
            rtau-=dtau

        if (rtau<ltau):
            print((mtau))
            q=False

        
    print("xi= ",xi(ti,mtau))
    input()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
