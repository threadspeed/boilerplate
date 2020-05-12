---
title: python script loto 34 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'loto 34'


Modules used in program: 
* `import random`

## python loto 34

Python example: loto 34

```python
#version pour python <= 3.4

import random

#l'utilisateur entre ses 3 numeros
n1 = int(input('entrez votre premier numero (entre 0 et 20): '))
n2 = int(input('entrez votre second numero (entre 0 et 20): '))
n3 = int(input('entrez votre troisieme numero (entre 0 et 20): '))


#on tire au sort les 3 bons numeros
r1 = random.choice(range(21))
r2 = random.choice(range(21))
r3 = random.choice(range(21))

while r1 == r2 or r1 == r3 or r2 == r3:
	
	r1 = random.choice(range(21))
	r2 = random.choice(range(21))
	r3 = random.choice(range(21))
	
r = [r1, r2, r3]

#comparaisons
z = 0  #cest le nombre de bons numeros trouves

for i in r:
	
	if i == n1 or i == n2 or i == n3:
		
		z = z + 1
		
#affichage du resultat
if z < 3:
	
	print(('vous avez perdu'))
	
	
elif z == 3:
	
	print(('vous avez gagné') )
	



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
