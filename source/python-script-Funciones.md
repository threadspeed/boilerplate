---
title: python script Funciones (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Funciones'

Functions in program: 
* `def curar(self, curado_por=2, curacion_completa=True):`
* `def ataque_aleatorio(jugador1, jugador2):`

Modules used in program: 
* `import random`

## python Funciones

Python mysql example: Funciones

```python
import random
def ataque_aleatorio(jugador1, jugador2):
    porcentaje_ataque = 5 * [id(jugador1)] + 5 * [id(jugador2)]
    seleccion = random.choice(porcentaje_ataque)
    if seleccion == id(jugador1):
        return jugador1
    return jugador2

def curar(self, curado_por=2, curacion_completa=True):

    if self.medidor_salud == self.max_salud:
        return self.medidor_salud
    elif curacion_completa:
        self.medidor_salud = self.max_salud
    else:
        self.medidor_salud += curado_por

    if self.medidor_salud > self.max_salud:
        self.medidor_salud = self.max_salud
    print("¡Has sido curado!")
    self.mostrar_salud(bold=True)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
