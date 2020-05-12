---
title: python script loto numpy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'loto numpy'


Modules used in program: 
* `import numpy as np`

## python loto numpy

Python example: loto numpy

```python
import numpy as np

#l'utilisateur entre ses 3 numeros
n = input('entrez vos 3 numeros (entre 0 et 20 séparés par des virgules ou des espaces): ')

x = sorted([int(i) for i in n.replace(" ", ",").strip(" ").split(",") if i != ''])

#on tire au sort les 3 bons numeros
r = sorted(np.random.choice(range(21),3,replace=False))

#comparaison et affichage du resultat
if x == list(r):
	print(('vous avez gagné'))
	
else:
	print(('vous avez perdu'))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
