---
title: python script Programmierkurs %25C3%259Cbungen Programmierkurs u eingabe gehalt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Programmierkurs %25C3%259Cbungen Programmierkurs u eingabe gehalt'


## python Programmierkurs %25C3%259Cbungen Programmierkurs u eingabe gehalt

Python mysql example: Programmierkurs %25C3%259Cbungen Programmierkurs u eingabe gehalt

```python
 # coding: latin-1

#Bruttogehalt einlesen
print("Bitte geben Sie Ihr monatliches Bruttogehalt ein:")
b = input()
brutto = int(b)

#Familienstand einlesen
print("Bitte geben Sie 1 für verheiratet oder 0  für ledig ein")
f = input()
familienstand = int(f)

#Steuersatz berechnen
if (brutto > 4000) and (familienstand == 1):
    s = 26
elif (brutto > 400) and (familienstand == 0):
    s = 22
elif (brutto <= 4000) and (familienstand == 1):
    s = 22
else:
    s = 18
steuersatz = int(s)

#Berechnung und Ausgabe der Steuern
steuerbetrag = ((brutto/100)* steuersatz)

print("Es ergibt sich ein monatlicher Steuersatz von: ",steuerbetrag)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
