---
title: python script Satzgenerator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Satzgenerator'

Functions in program: 
* `def out(txt):`

Modules used in program: 
* `import subprocess as su`
* `import sys`
* `import random`
* `import pickle`
* `import os`

## python Satzgenerator

Python example: Satzgenerator

```python
#python 3
import os
import pickle
import random
import sys
import subprocess as su
#variablen______________________________
verb ={}
adj={}
nom={} 
loop=True
weiterfuerung=False
#variablen______________________________
#Datenbanken°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°
with open("nom.adb","rb") as nomfile:
    nom=pickle.load(nomfile)
with open("verb.adb","rb") as verbfile:
    verb=pickle.load(verbfile)
with open("adj.adb","rb") as adjfile:
    adj=pickle.load(adjfile)
#Datenbanken°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°
#definitionen^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
def out(txt):
        print(txt)
        su.call(["espeak","-v","german",txt])
#definitionen^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
if len(sys.argv)>1:        
    if sys.argv[1].isdigit():
        numsaetze=int(sys.argv[1])
        loop=False

while loop:
    numsaetze=input("Wie viele Sätze willst du ?\n>")
    try:
        numsaetze=int(numsaetze)
        break 
    except:
        print("Bitte eine Zahl eingeben!")

#Class 1:
#artikel Nomen verb adjektiv
for x in range(numsaetze):
    subjekt=random.choice(list(nom.keys()))
    praedikat=random.choice(list(verb.keys()))
    if nom[subjekt][0]=="p":
        artikel="Die"
        if verb[praedikat][0]=="u":
            praedikat=verb[praedikat][-1]
        else:
            praedikat=verb[praedikat][1]+"en"
    else:#sublekt singular
        if nom[subjekt][1]=="m":
            artikel="Der"
        elif nom[subjekt][1]=="f":
            artikel="Die"
        else:
            artikel="Das"
        if verb[praedikat][0]=="u":
            praedikat=verb[praedikat][-4]
        else:
            praedikat=verb[praedikat][1]+"t"
    adjektiv=random.choice(list(adj.keys()))
    if random.random()<=0.5:
        sprech ="'{} {} {} {}.'".format(artikel,subjekt,praedikat,adjektiv)
        out(sprech)
    else:
        print(artikel,subjekt,praedikat,adjektiv+", weil ",end="")
        subjekt=random.choice(list(nom.keys()))
        praedikat=random.choice(list(verb.keys()))
        subjekt2=random.choice(list(nom.keys()))
        if nom[subjekt][0]=="p":
            artikel="die"
            if verb[praedikat][0]=="u":
                praedikat=verb[praedikat][-1]
            else:
                praedikat=verb[praedikat][1]+"en"
        else:#sublekt singular
            if nom[subjekt][1]=="m":
                artikel="der"
            elif nom[subjekt][1]=="f":
                artikel="die"
            else:
                artikel="das"
            if verb[praedikat][0]=="u":
                praedikat=verb[praedikat][-4]
            else:
                praedikat=verb[praedikat][1]+"t"
        adjektiv=random.choice(list(adj.keys()))
        #print(artikel,subjekt,adjektiv,subjekt2,praedikat+".")
        sprech ="'{} {} {} {} {}.'".format(artikel,subjekt,adjektiv,subjekt2,praedikat)
        out(sprech)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
