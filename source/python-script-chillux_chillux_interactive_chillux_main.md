---
title: python script chillux chillux interactive chillux main (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'chillux chillux interactive chillux main'

Functions in program: 
* `def menu():`
* `def make():`
* `def slow_print(string):`

Modules used in program: 
* `import getpass`
* `import sys`
* `import time`
* `import datetime`
* `import random`
* `import os`

## python chillux chillux interactive chillux main

Python example: chillux chillux interactive chillux main

```python
import os
import random
import datetime
import time
import sys
import getpass

def slow_print(string):
    for letter in string:
        sys.stdout.write(letter)
        sys.stdout.flush()
        time.sleep(.10)

userName = getpass.getuser()
# slow_print(">> Hola ")
# slow_print(userName)
# slow_print("\n>> Chillux es un asistente que pretende ahorrarte tiempo ejecutando por ti tareas en la terminal\n")
# slow_print(">> A continuación te mostraré una serie de opciones que puedes escojer según lo que necesites hacer\n")
def make():
    print("1- Carpeta"
          "2- Archivo")

def menu():
    options ={
        1: "make",
        2: "Modificar",
        3: "Copiar",
        4: "Mover",
        5: "Informacion"
    }
    print(options)

choose = input()
if (choose==1):
    print("Hola")



menu()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
