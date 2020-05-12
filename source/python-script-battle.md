---
title: python script battle (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'battle'


Modules used in program: 
* `import random`

## python battle

Python mysql example: battle

```python
#Battle a random Enemy with Simple 
#Fallout-like system by Caberfries


#Player and Enemy HP and Defense stats
import random
enemyhp = random.choice([50, 30, 20])
hp = 50
defense = 10


while (enemyhp) >= 0:
	#Player attack stats 
	import random
	legs = random.randint (3, 5)
	arms = random.randint (1,6)
	chest = random.choice ([0, 10])
	head = random.choice ([0, 15])
	
	#Enemy attack stats
	enemydmg = random.choice ([0, 1,  5, 7, 10])

	#Battle menu
	print"HP:", hp	
	print"Defense:", defense

	print("""
	    ~~~~~~~~~~~~~~
		Battle
	    ~~~~~~~~~~~~~~

	    Choose wisely:

	    0 ~ Attack legs (3-5 dmg)
	    1 ~ Attack arms (1-6 dmg)
	    2 ~ Attack chest (1 or 8 dmg)
	    3 ~ Attack head (Miss or Critical(15 dmg)
	    4 ~ Defend (Get defense boost but take damage)
	    """)

	choice = input("Choice: ")


	#Conditional Battle 
	if choice == '0':
		print"Your health is", hp
		print"Enemy health is", enemyhp
		enemyhp = enemyhp-legs
		print"You did", legs, "damage!"
		print"Enemy has", enemyhp, "health left!"

	if choice == '1':
		print"Your health is", hp
		print"Enemy health is", enemyhp
		enemyhp = enemyhp-arms
		print"You did", arms, "damage!"
		print"Enemy has", enemyhp, "health left!"

	if choice == '2':
		print"Your health is", hp
		print"Enemy health is", enemyhp
		enemyhp = enemyhp-chest
		print"You did", chest, "damage!"
		print"Enemy has", enemyhp, "health left!"

	if choice == '3':
		print"Your health is", hp
		print"Enemy health is", enemyhp
		enemyhp = enemyhp-head
		print"You did", head, "damage!"
		print"Enemy has", enemyhp, "health left!"

	if choice == '4':
		hp = hp+defense
		print"Your health is", hp

	#Enemy turn
	if enemyhp > 0:
		hp = hp-enemydmg
		print"Enemy did", enemydmg, "damage!"
		print"You have", hp, "health left!"
		
	#Enemy death
	while enemyhp <= 0:
		

		if enemyhp <= 0:
			print("""
			~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
					VICTORY
			~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
			""")
		
			exit(0)
			
	
		#Player death
		while hp <= 0:

	
			if hp <= 0:
				print("""

		~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
				DEATH
		~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
		""")
		exit(0)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
