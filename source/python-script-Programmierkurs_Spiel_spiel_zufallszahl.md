---
title: python script Programmierkurs Spiel spiel zufallszahl (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Programmierkurs Spiel spiel zufallszahl'


Modules used in program: 
* `import random`

## python Programmierkurs Spiel spiel zufallszahl

Python example: Programmierkurs Spiel spiel zufallszahl

```python
#Modul random Importieren
import random

#Zufallsgenerator initialisieren
random.seed()

a = random.randint(1,10)
b = random.randint(1,10)
c = a+b

print("Die Aufgabe:", a, "+", b)

#Eingabe
print("Bitte eine Zahl eingeben:")

z = input()
zahl = int(z)

#Verzweigung
if zahl ==c:
    print(zahl, "ist richtig")
else:
    print(zahl, "ist falsch")
    print("Ergebnis:", c)





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
