---
title: python script ugani glavno mesto zanka (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ugani glavno mesto zanka'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python ugani glavno mesto zanka

Python example: ugani glavno mesto zanka

```python
# -*- coding: utf-8 -*-

import random

def main():
    skrivno_stevilo = random.randint(1, 50)

    while True:
        ugani_stevilo = int(raw_input("Ugani skrivno stevilo med 1 and 50: "))

        if ugani_stevilo == skrivno_stevilo:
            print("PRAVILNO -  Skrivno stevilo je %s :" % skrivno_stevilo)
            break

        elif ugani_stevilo > skrivno_stevilo:

            print("NAPAKA, tvoje stevilo je preveliko...poskusi ponovno.")

        elif ugani_stevilo < skrivno_stevilo:

            print("NAPAKA, tvoje stevilo je prenizko...poskusi ponovno.")





if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
