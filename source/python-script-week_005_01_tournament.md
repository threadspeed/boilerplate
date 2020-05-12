---
title: python script week 005 01 tournament (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 005 01 tournament'

Functions in program: 
* `def tournament():`
* `def fight(first, second, prize):`
* `def assess_hero(knight):`
* `def hero():`

Modules used in program: 
* `import random`

## python week 005 01 tournament

Python mysql example: week 005 01 tournament

```python
import random

def hero():
    strength = random.randint(0, 15)
    agility = random.randint(0, 15 - strength)
    intelligence = random.randint(0, 15 - strength - agility)
    endurance = random.randint(0, 15 - strength - agility - intelligence)
    charisma = random.randint(0, 15 - strength - agility - intelligence - endurance)
    # print(("Параметры рыцаря:\nСила: %s \nЛовкость: %s \nИнтеллект: %s \nВыносливость: %s \nХаризма: %s" % (strength, agility, intelligence, endurance, charisma)))

    attack_damage = strength * 3 + agility * 2
    health = endurance * 4 + strength 
    can_carry = endurance * 2 + strength * 3
    eloquence = charisma * 4 + intelligence
    # print(("\nНавыки рыцаря:\nУрон: %s\nЗдоровье: %s\nПереносимый вес: %s\nКрасноречие: %s" % (attack_damage, health, can_carry, eloquence)))
	
    return {'Урон' : attack_damage, 'Здоровье' : health, 'Переносимый вес' : can_carry, 'Интеллект' : intelligence, 'Харизма' : charisma}
	
def assess_hero(knight):
	print(knight)
	for_king = knight['Урон'] + knight['Здоровье'] + knight['Переносимый вес']
	for_princess = knight['Интеллект'] * knight['Харизма']
	return for_king, for_princess

def fight(first, second, prize):
	if first > second:
		winner = "The first knight"
	elif first < second:
		winner = "The second knight"
	else:
		winner = "No one"
	print('%s wins the %s' % (winner, prize))
	
def tournament():
	first = hero()
	second = hero()
	
	judgement_k_first, judgement_pr_first = assess_hero(first)
	judgement_k_second, judgement_pr_second = assess_hero(second)
	
	fight(judgement_k_first, judgement_k_second, "king's award")
	fight(judgement_pr_first, judgement_pr_second, "princess's heart")
	


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
