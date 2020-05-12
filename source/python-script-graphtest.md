---
title: python script graphtest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'graphtest'

Functions in program: 
* `def random_key(x):`

Modules used in program: 
* `import nametest as nt`
* `import random`

## python graphtest

Python mysql example: graphtest

```python
import random
import nametest as nt


def random_key(x):
	return random.choice(list(x.keys()))
	
graph = {
	"Rustblood": {
		"Derse Dreamer": {
			"True Aries": {
				"Time": {}
			
			},
			"Arsces": {
				"Life": {}
			
			},
			"Arrius": {
				"Hope": {}
			
			},
			"Ariborn": {
				"Rage": {}
				
			},
			"Arittarius": {
				"Void": {}
			
			},
			"Arpia": {
				"Light": {}
			
			},
			"Arza": {
				"Mind": {}
			
			},
			"Arga": {
				"Space": {}
				
			},
			"Aro": {
				"Heart": {}
			
			},
			"Arcen": {
				"Blood": {}
			
			},
			"Armini": {
				"Doom": {}
			
			},
			"Arun": {
				"Breath": {}
				
			},
		},
		"Prospit Dreamer": {
			"Arist": {
				"Time": {}
			
			},
			"Arsci": {
				"Life": {}
			
			},
			"Arnius": {
				"Hope": {}
			
			},
			"Aricorn": {
				"Rage": {}
				
			},
			"Arittanius": {
				"Void": {}
			
			},
			"Arpio": {
				"Light": {}
			
			},
			"Arra": {
				"Mind": {}
			
			},
			"Argo": {
				"Space": {}
				
			},
			"Argo": {
				"Heart": {}
			
			},
			"Arcer": {
				"Blood": {}
			
			},
			"Armino": {
				"Doom": {}
			
			},
			"Arus": {
				"Breath": {}
				
			},
		},
	},
	"Bronzeblood": {
		"Derse Dreamer": {
			"Taurun": {
				"Breath": {}
			
			},
			"Tauries": {
				"Time": {}
			
			},
			"Taursces": {
				"Life": {}
			
			},
			"Taurrius": {
				"Hope": {}
			
			},
			"Tauriborn": {
				"Rage": {}
			
			},
			"Taurittarius": {
				"Void": {}
			
			},
			"Taurpia": {
				"Light": {}
			
			},
			"Taurza": {
				"Mind": {}
			
			},
			"Taurga": {
				"Space": {}
			
			},
			"Tauro": {
				"Heart": {}
			
			},
			"Taurcen": {
				"Blood": {}
			
			},
			"Taurmini": {
				"Doom": {}
			
			},
		},
		"Prospit Dreamer": {
			"True Taurus": {
				"Breath": {}
			
			},
			"Taurist": {
				"Time": {}
			
			},
			"Taursci": {
				"Life": {}
			
			},
			"Taurnius": {
				"Hope": {}
			
			},
			"Tauricorn": {
				"Rage": {}
			
			},
			"Taurittanius": {
				"Void": {}
			
			},
			"Taurpio": {
				"Light": {}
			
			},
			"Taurra": {
				"Mind": {}
			
			},
			"Taurgo": {
				"Space": {}
			
			},
			"Taurlo": {
				"Heart": {}
			
			},
			"Taurcer": {
				"Blood": {}
			
			},
			"Taurmino": {
				"Doom": {}
			
			},
		},
	},
	"Goldblood": {
		"Derse Dreamer": {
			"True Gemini": {
				"Doom": {}
			
			},
			"Gemun": {
				"Breath": {}
			
			},
			"Gemries": {
				"Time": {}
			
			},
			"Gemsces": {
				"Life": {}
			
			},
			"Gemrius": {
				"Hope": {}
			
			},
			"Gemiborn": {
				"Rage": {}
			
			},
			"Gemittarius": {
				"Void": {}
			
			},
			"Gempia": {
				"Light": {}
			
			},
			"Gemza": {
				"Mind": {}
			
			},
			"Gemga": {
				"Space": {}
			
			},
			"Gemo": {
				"Heart": {}
			
			},
			"Gemcen": {
				"Blood": {}
			
			},
		},
		"Prospit Dreamer": {
			"Gemino": {
				"Doom": {}
			
			},
			"Gemus": {
				"Breath": {}
			
			},
			"Gemrist": {
				"Time": {}
			
			},
			"Gemsci": {
				"Life": {}
			
			},
			"Gemnius": {
				"Hope": {}
			
			},
			"Gemicorn": {
				"Rage": {}
			
			},
			"Gemittanius": {
				"Void": {}
			
			},
			"Gempio": {
				"Light": {}
			
			},
			"Gemra": {
				"Mind": {}
			
			},
			"Gemgo": {
				"Space": {}
			
			},
			"Gemlo": {
				"Heart": {}
			
			},
			"Gemcer": {
				"Blood": {}
			
			},
		},
	},
}

choices = []

classselection = ["Heir","Witch","Mage","Prince","Bard","Seer","Maid","Thief","Rogue","Knight","Sylph","Page"]

level = graph

while level:
	key = random_key(level)
	level = level[key]
	choices.append(key)

nt.namecall()	

classpect = "Your classpect is the {} of {},".format(random.choice(classselection), choices[3])

signsway = "your sign is {} which is under the {} signs. \nThis makes you a {}!".format(choices[2], choices[0].replace("blood",""), choices[1])

message = "The generator has spoken.\nYour name is {}! \n{} and {}".format(nt.printname(),classpect, signsway)

print(message)





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
