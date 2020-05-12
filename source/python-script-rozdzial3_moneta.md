---
title: python script rozdzial3 moneta (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rozdzial3 moneta'


Modules used in program: 
* `import random`

## python rozdzial3 moneta

Python mysql example: rozdzial3 moneta

```python
import random

orzel = 0
reszka = 0
rzut = 0

while rzut != 100:
    moneta = random.randint(1,2)
    if moneta == 1:
        orzel += 1
    else:
        reszka += 1
    rzut += 1

print("Wyrzucono", orzel, "razy orła i", reszka, "razy reszkę")
input("\n\nAby zakończyć program, naciśnij klawisz Enter")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
