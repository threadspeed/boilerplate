---
title: python script Guerrero (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Guerrero'


## python Guerrero

Python mysql example: Guerrero

```python
from Proyecto_final.Player import Player
from Proyecto_final import Funciones

class Guerrero(Player):
    def __init__(self, nombre_jugador, edad, genero):
        Player.__init__(self, nombre_jugador)
        self.edad = edad
        self.nombre_jugador = nombre_jugador
        self.genero = genero
        self.max_salud = 100
        self.medidor_salud = self.max_salud
        self.tipo_jugador = 'Amigo'

    def rendirse():
        return 'Se ha rendido!'

    def __repr__(self):
        return "¡Mi nombre es " + self.nombre_jugador + " Soy un guerrero valiente!, mi nivel de vida es " + str(self.medidor_salud)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
