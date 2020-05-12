---
title: python script loto (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'loto'


Modules used in program: 
* `import random`

## python loto

Python mysql example: loto

```python
#version pour python >= 3.5

import random

#l'utilisateur entre ses 3 numeros
n1 = int(input('entrez votre premier numero (entre 0 et 20): '))
n2 = int(input('entrez votre second numero (entre 0 et 20): '))
n3 = int(input('entrez votre troisieme numero (entre 0 et 20): '))


#on tire au sort les 3 bons numeros
r = random.choices(range(21),k=3)


while r[0] == r[1] or r[0] == r[2] or r[1] == r[2]:
	
	r = random.choices(range(21),k=3)
	


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
