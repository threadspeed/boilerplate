---
title: python script ugani glavno mesto (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ugani glavno mesto'

Functions in program: 
* `def preveri_izbor(uporabnikovo_ugibanje, drzava, g_mesto):`
* `def main():`

## python ugani glavno mesto

Python example: ugani glavno mesto

```python
def main():
    glavno_mesto_drzave = {"Slovenija-e": "Ljubljana", "Hrvatska-e": "Zagreb", "Srbija-a": "Beograd"}

    while True:
        izbrana_drzava = glavno_mesto_drzave.keys()[1]
        ugani = raw_input("Katero je glavno mesto %s" % izbrana_drzava)
        preveri_izbor(ugani, izbrana_drzava, glavno_mesto_drzave)   # POGLEJ VRSTNI RED FUNKCIJE SPODAJ:  def preveri_izbor
        nadaljevanje = raw_input("Ali bi hotel nadaljevati? (da/ne")
        if nadaljevanje == "ne":
            break

        print("Konec")

def preveri_izbor(uporabnikovo_ugibanje, drzava, g_mesto):
    prestolnica = g_mesto[drzava]

    if uporabnikovo_ugibanje == prestolnica:
        print("PRAVILNO! Prestolnica %s je %s." % (drzava, prestolnica))
        return True
    else:
        print("NAPACEN ODGOVOR. Prestolnica %s je %s." % (drzava, prestolnica))
        return False

if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
