---
title: python script rozdzial3 jaka to liczba (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rozdzial3 jaka to liczba'


Modules used in program: 
* `import random`

## python rozdzial3 jaka to liczba

Python mysql example: rozdzial3 jaka to liczba

```python
import random

print("\tWitaj w grze 'Jaka to liczba'!")
print("\nMam na myśli pewną liczbę z zakresu od 1 do 100.")
print("Spróbuj ją odgadnąć w jak najmniejszej liczbie prób.\n")

the_number = random.randint(1, 100)
guess = int(input("Ta liczba to: "))
tries = 1

while guess != the_number:
    if guess > the_number:
        print("Za duża...")
    else:
        print("Za mała...")

    guess = int(input("Ta liczba to: "))
    tries += 1

print("Odgadłeś! Ta liczba to:", the_number)
print("Do osiągnięcia sukcesu potrzebowałeś tylko", tries, "prób!\n")
input("\n\nAby zakończyć program, naciśnij klawisz Enter")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
