---
title: python script Seminararbeit Bin%25C3%25A4re%2520Suche V3%2520(mit%2520Laufzeitbereichnung (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Seminararbeit Bin%25C3%25A4re%2520Suche V3%2520(mit%2520Laufzeitbereichnung'

Functions in program: 
* `def zufallsListeBuchstabenDoppelt(n):`

Modules used in program: 
* `import time`
* `import random`
* `import string`

## python Seminararbeit Bin%25C3%25A4re%2520Suche V3%2520(mit%2520Laufzeitbereichnung

Python example: Seminararbeit Bin%25C3%25A4re%2520Suche V3%2520(mit%2520Laufzeitbereichnung

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

zeiten = []
zeiten_durchschnitte = []

laenge_der_tests = [1, 3, 4, 5, 10, 15, 20, 25, 50, 100, 150, 200, 400, 800, 1200, 2400, 3600, 4800, 9600, 19200, 38400]
dauer_der_test = []

for t in laenge_der_tests:
    tstart = time.time()
    zeiten = []

    for i in range(1, 100):

        unsortierte_liste = zufallsListeBuchstabenDoppelt(t)
        liste = sorted(unsortierte_liste)
        suchElement = "DB"
        last = len(liste) - 1
        first = 0
        middle = last // 2
        #print(unsortierte_liste)
        #print(liste)
        t1 = time.time()

        while True:

            if first == last or first == last + 1 or first + 1 == last:
                print(str(i)+" - Kein Ergebnis")
                t2 = time.time()
                break
            elif liste[middle] == suchElement:
                print(str(i)+" - Das gesuchte Element "+str(suchElement)+" befindet sich (unter anderem) an der Position "+str(middle))
                t2 = time.time()
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
                break

        zeit = (t2 - t1)
        zeiten.append(zeit)

    zeiten_durchschnitte.append(sum(zeiten)/len(zeiten))

print(zeiten_durchschnitte)

x=0
while True:
    eindurchschnitt = zeiten_durchschnitte[x]
    print(str(eindurchschnitt))
    x += 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
