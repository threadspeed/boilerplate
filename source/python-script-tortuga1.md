---
title: python script tortuga1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tortuga1'

Functions in program: 
* `def juego():`
* `def num_dados(n):`
* `def lanzar_dado():`

Modules used in program: 
* `import random`

## python tortuga1

Python example: tortuga1

```python
# -*- coding: utf-8 -*-
import random

def lanzar_dado():
	return 1 + random.randrange(6)

def num_dados(n):
	lista = []
	for i in range(n):
		lista += [lanzar_dado()]
	return lista

def juego():
	caparazon = False
	patas = False
	num_patas = 0
	jugadas = 3
	n = 5
	while jugadas > 0:
		dados = num_dados(n)
		print(dados)
		if caparazon:
			if 1 in dados:
				patas = True
				for i in dados:
					if i == 1:
						num_patas += 1
						n -= 1
		elif 6 in dados:
			caparazon = True
			n -= 1
			if 1 in dados:
				patas = True
				for i in dados:
					if i == 1:
						num_patas += 1
						n -= 1
		if caparazon == True:
			print("Tengo el caparazón")
			if patas == True:
				if num_patas < 2:
					print("Tengo", num_patas, "pata")
				elif num_patas >= 2:
					print("Tengo", num_patas, "patas")
		else:
			print("No tengo nada")
		jugadas -= 1

juego()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
