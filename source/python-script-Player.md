---
title: python script Player (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Player'


Modules used in program: 
* `import random`

## python Player

Python mysql example: Player

```python
from Proyecto_final.Funciones import ataque_aleatorio
from Proyecto_final.Player import Player
import random

class Player:
    '''
    Clase jugador
    '''
    def __init__(self, nombre_jugador =''):
        self.max_salud = 0
        self.medidor_salud = 0
        self.nombre_jugador = nombre_jugador
        self.tipo_jugador = None

    def atacar(self, enemigo):
        '''
        Función para definir daño aleatorio que se genera hacia el Vikingo o el guerrero.
        :param enemigo: Vikingo del juego
        :return:
        '''
        jugador_herido = ataque_aleatorio(self.tipo_jugador)
        herida = random.randint(10, 15)
        jugador_herido.medidor_salud = max(jugador_herido.Medidor_salud - herida, 0)
        print("¡Ataque! ")
        self.mostrar_salud()
        enemigo.mostrar_salud()

    def reset_medidor_salud(self):
        '''
        Función que uelve la salud al estado original
        :return:  
        '''
        salud = self.medidor_salud = self.max_salud
        return salud

    def mostrar_salud(self):
        '''
        Funcion que arroja la salud que tinene el enemigo y el guerrero
        :return: salud del jugador
        '''
        msg = "Salud: %s: %d" % (self.nombre_jugador, self.medidor_salud)
        print(msg)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
