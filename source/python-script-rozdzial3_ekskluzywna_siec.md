---
title: python script rozdzial3 ekskluzywna siec (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rozdzial3 ekskluzywna siec'


## python rozdzial3 ekskluzywna siec

Python example: rozdzial3 ekskluzywna siec

```python
print("\tEkskluzywna Sieć Komputerowa")
print("\t   Tylko dla członków")

security = 0

username = ""
while not username:
    username = input("Użytkownik: ")

password = ""
while not password:
    password = input("Hasło: ")

if username == "M.Dawson" and password == "sekret":
    print("Cześć, Mike")
    security = 5
elif username == "S.Meier" and password == "cywilizacja":
    print("Cześć, Sid")
    security = 3
elif username == "S.Miyamoto" and password == "mariobros":
    print("Co u Ciebie, Shigeru?")
    security = 3
elif username == "W.Wright" and password == "simowie":
    print("Jak leci, Will?")
    security = 3
elif username == "gość" and password == "gość":
    print("Witaj, gościu.")
    security = 1
else:
    print("Nieudana próba logowania. Nie jesteś taki wyjątkowy.\n")

print("\n\nAby zakończyć program, naciśnij klawisz Enter")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
