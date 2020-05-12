---
title: python script lotto (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lotto'

Functions in program: 
* `def lotto():`
* `def wprowadz_liczbe():`

Modules used in program: 
* `import random`

## python lotto

Python example: lotto

```python
import random

moje_lotto = []
kulki = [x for x in range(1,50)]
random.shuffle(kulki)
wynik_losowania = kulki[0:6]
wynik_losowania.sort()

def wprowadz_liczbe():
    liczba = input("Wprowadz liczbe: ")
    try:
        liczba = int(liczba)
        if liczba>0 and liczba<=49:
            return liczba
    except:
        return None


def lotto():
    print(f"Wynik losowania: {wynik_losowania}")

    while len(moje_lotto)<6:
        los = wprowadz_liczbe()
        if (los is not None) and (los not in moje_lotto):
            moje_lotto.append(los)
        else:
            print("Wprowadziłeś niepoprawną liczbę")

    moje_lotto.sort()
    print(f"Mój kupon: {moje_lotto}")
    print(f"Wynik losowania: {wynik_losowania}")

    liczba_trafionych = 0

    for l in moje_lotto:
        if l in wynik_losowania:
            liczba_trafionych += 1

    if liczba_trafionych>=3:
        print((f"Trafiłeś {liczba_trafionych} liczb!"))

lotto()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
