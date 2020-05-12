---
title: python script lotto2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lotto2'

Functions in program: 
* `def lotto():`
* `def wprowadz_kupon():`
* `def wprowadz_liczbe():`
* `def wylosuj_liczby():`

Modules used in program: 
* `import random`

## python lotto2

Python mysql example: lotto2

```python
import random


def wylosuj_liczby():
    liczby = random.sample([n for n in range(1, 50)], 6)
    liczby.sort()
    return liczby


def wprowadz_liczbe():
    liczba = input("Wprowadz liczbe: ")
    try:
        liczba = int(liczba)
        if liczba>0 and liczba<=49:
            return liczba
    except:
        return None


def wprowadz_kupon():
    moje_lotto = []

    while len(moje_lotto)<6:
        los = wprowadz_liczbe()
        if (los is not None) and (los not in moje_lotto):
            moje_lotto.append(los)
        else:
            print("Wprowadziłeś niepoprawną liczbę")

    moje_lotto.sort()
    return moje_lotto


def lotto():
    wynik_losowania = wylosuj_liczby()
    kupon = wprowadz_kupon()

    print(f"Mój kupon: {kupon}")
    print(f"Wynik losowania: {wynik_losowania}")

    lista_trafionych = [x for x in kupon if x in wynik_losowania]

    if (len(lista_trafionych)>3):
        print((f"Gratulacje wygranej! Trafiłeś następujące liczby: {lista_trafionych}"))
    else:
        print(f"Niestety nic nie wygrałeś. Trafione: {lista_trafionych}")


lotto()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
