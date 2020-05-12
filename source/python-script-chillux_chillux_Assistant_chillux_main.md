---
title: python script chillux chillux Assistant chillux main (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'chillux chillux Assistant chillux main'

Functions in program: 
* `def cleanWindow():`
* `def showTime():`
* `def networkInf():`
* `def makeDir():`
* `def askWish():`
* `def welcome():`

Modules used in program: 
* `import random`
* `import os`
* `import datetime`

## python chillux chillux Assistant chillux main

Python mysql example: chillux chillux Assistant chillux main

```python
import datetime
import os
import random

from chillux_Assistant import chillux_arrays


def welcome():
    os.system("echo 'Hola,' `whoami`'!!!'")

def askWish():
    ranAsk = random.randint(1, chillux_arrays.asks.__len__() - 1)
    wish = input(chillux_arrays.asks[ranAsk])
    if (str.lower(wish) in chillux_arrays.makedirsAns):
        makeDir()
    elif (str.lower(wish) in chillux_arrays.netInf):
        networkInf()
    elif (str.lower(wish) in chillux_arrays.askHour):
        showTime()
    elif (str.lower(wish) in chillux_arrays.cleanWindow):
        cleanWindow()


def makeDir():
    rute = input("Inserta la ruta donde quieres crear la carpeta [inserta '/' luego del ultimo elemento de la ruta]: ")
    folder = input("Inserta el nombre de la carpeta: ")
    os.system("mkdir "+rute+folder)
    print("La carpeta " + folder + " ha sido creada con exito")
    askList = input("Deseas que liste los diferentes elementos en la ruta especificada?[si/no]: ")
    if (str.lower(askList)=="si"):
        def showDet():
            detail = input("Deseas una informacion detallada o simple(solo los nombres de las carpetas)[detallada/simple]: ")
            if (detail == "simple"):
                os.system("ls " + rute)
                askWish()
            elif (detail == "detallada"):
                os.system("ls -l " + rute)
                askWish()
            else:
                print("Al parecer has escrito una palabra incorrecta, por favor vuelve a insertar la palabra")
                showDet()
        showDet()
    else:
        askWish()

def networkInf():
    os.system("ifconfig")
    askWish()

def showTime():
    print("Aqui tienes la hora: ", datetime.datetime.now().strftime("%H:%M:%S"))
    hora = datetime.datetime.now().hour
    if (hora < 5 or hora > 21):
        print("Es muy tarde, deberias dormir")
    elif (hora>=5 and hora<12):
        print("Buenos dias")
    elif (hora>=12 and hora<21):
        print("Buenas tardes")
    askWish()

def cleanWindow():
    os.system("clear")
    askWish()

welcome()
askWish()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
