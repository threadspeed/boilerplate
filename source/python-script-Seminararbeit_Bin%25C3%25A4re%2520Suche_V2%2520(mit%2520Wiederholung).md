---
title: python script Seminararbeit Bin%25C3%25A4re%2520Suche V2%2520(mit%2520Wiederholung) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Seminararbeit Bin%25C3%25A4re%2520Suche V2%2520(mit%2520Wiederholung)'

Functions in program: 
* `def zufallsListeBuchstabenDoppelt(n):`

Modules used in program: 
* `import time`
* `import random`
* `import string`

## python Seminararbeit Bin%25C3%25A4re%2520Suche V2%2520(mit%2520Wiederholung)

Python example: Seminararbeit Bin%25C3%25A4re%2520Suche V2%2520(mit%2520Wiederholung)

```python
from random import *
import string
import random
import time


def zufallsListeBuchstabenDoppelt(n):
    liste = []
    for i in range(n):
        liste.append(random.choice(string.ascii_uppercase)+(random.choice(string.ascii_uppercase)))
    return liste


#Achtung: Keine/zu wenig Abbruch-Bedingungen definiert.

positionen = []
zeiten = []

for i in range(1, 100):

    unsortierte_liste = zufallsListeBuchstabenDoppelt(2000)
    liste = sorted(unsortierte_liste)
    suchElement = "DB"
    last = len(liste) - 1
    first = 0
    middle = last // 2
    #print(unsortierte_liste)
    #print(liste)
    t1 = time.time()

    while True:

        if first == last:
            print(str(i)+" - Kein Ergebnis")
            t2 = time.time()
            positionen.append(2001)
            break
        elif liste[middle] == suchElement:
            print(str(i)+" - Das gesuchte Element "+str(suchElement)+" befindet sich (unter anderem) an der Position "+str(middle))
            t2 = time.time()
            positionen.append(middle)
            break
        elif suchElement < liste[middle]:
            last = middle -1
            middle = first + (last - first)//2
        elif suchElement > liste[middle]:
            first = middle+1
            middle = first + (last - first)//2
        else:
            #print("Uh, oh, etwas hat nicht funktioniert")
            t2 = time.time()
            positionen.append(2001)
            break

    zeit = (t2 - t1)
    zeiten.append(zeit)

print(zeiten)
print(positionen)

#Laufzeiten analysieren:

durchschnitt = sum(zeiten)/len(zeiten)
langsam = 0
schnell = 10
for i in zeiten:
    if i < schnell:
        schnell = i
    elif i > langsam:
        langsam = i

print("Schnellste Zeit:"+str(schnell))
print("Durchschnittliche Zeit:"+str(durchschnitt))
print("Langsamste Zeit:"+str(langsam))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
