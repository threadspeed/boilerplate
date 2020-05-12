---
title: python script Vikingo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Vikingo'


## python Vikingo

Python mysql example: Vikingo

```python
from Proyecto_final import Player
from Proyecto_final import Funciones

class Vikingo(Player):
    def __init__(self, Nombre = ''):
        Player.__init__(self, Nombre)
        self.max_salud = 100
        self.medidor_salud = self.max_salud
        self.tipo_jugador = 'enemigo'

    def info(self):
        return 'Soy un Vikingo, y hoy conquistare estas tierras'

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
