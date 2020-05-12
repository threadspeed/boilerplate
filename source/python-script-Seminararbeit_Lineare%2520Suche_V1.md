---
title: python script Seminararbeit Lineare%2520Suche V1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Seminararbeit Lineare%2520Suche V1'

Functions in program: 
* `def zufallsListeBuchstaben(n):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import random`
* `import string`

## python Seminararbeit Lineare%2520Suche V1

Python mysql example: Seminararbeit Lineare%2520Suche V1

```python

from random import *
import string
import random

#Zufälligi Initialen-Liste erstellen:

def zufallsListeBuchstaben(n):
    liste = []
    for i in range(n):
        zwischenspeicher = ""
        zwischenspeicher += random.choice(string.ascii_uppercase)
        zwischenspeicher += random.choice(string.ascii_uppercase)
        liste.append(zwischenspeicher)
    return liste

#liste_1 = zufallsListeBuchstaben(1000)
#print(string.ascii_letters)
#print(liste_1)

#Lineare Suche:

gesucht = "DB"

print("Gesucht wird: "+gesucht)

position = []
messwiederholungen = 1000

for j in range(0, messwiederholungen):
    liste_1 = zufallsListeBuchstaben(2000)
    for i in range(1, len(liste_1)):
        if liste_1[i] == gesucht:
            #print("Suchkriterium: "+str(liste_1[0])+". Übereinstimmung an Position "+str(i)+" gefunden.")
            position.append(i)
            break
    else:
        #print("Keine Übereinstimmung gefunden.")
        position.append(2001)

print(position)

vereinfachung = []

for p in position:
    q = p//10
    #print(q)
    vereinfachung.append(q)

print(vereinfachung)

vereinfachung_geordnet = vereinfachung
vereinfachung_geordnet.sort()
print(vereinfachung_geordnet)

from collections import Counter

dict = Counter(vereinfachung_geordnet)

print(dict)

#Counter sortieren
sorted_dict = (sorted(dict.items()))
print(sorted_dict)

#Counter to two lists
l1 = []
l2 = []
for key in sorted_dict:
    l1.append([key[0]])
    l2.append([key[1]])

print(l1)
print(l2)

#Als Grafik ausgeben:

import matplotlib.pyplot as plt

plt.plot(l1, l2) 
plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
