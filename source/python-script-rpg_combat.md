---
title: python script rpg combat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpg combat'


Modules used in program: 
* `import random`

## python rpg combat

Python mysql example: rpg combat

```python
#!/usr/bin/env python3
import random
from rpg.player import Hero as Player

Enemy = {"name": "enemy", "health": 22, "damage": 2, "defence": 0, "evade": 10}
print("1 to attack, 2 to charge, 3 to defend, 4 to check status")


while Enemy["health"] > 0 or Player.health > 0:
    choice = input()
    if choice == "1":
        if random.randint(0, 100) <= Enemy["evade"]:
            print("player misses the enemy")
        elif random.randint(0, 100) >= Enemy["evade"]:
            Enemy["health"] = Enemy["health"] + Enemy["defence"] - Player.damage
            print("player damage enemy,current health ", Enemy["health"])
        if random.randint(0, 100) <= Player.evade:
            print("enemy misses player")
        elif random.randint(0, 100) >= Player.evade:
            Player.health = Player.health + Player.defence - Enemy["damage"]
            print("enemy damage player,current health  ", Player.health)

    if choice == "2":
        Player.damage += 3
        print("player starts a charged strike, increasing dmg to:", Player.damage)
        if random.randint(0, 100) <= Player.evade:
            print("enemy misses player")
        elif random.randint(0, 100) >= Player.evade:
            Player.health = Player.health + Player.defence - Enemy["damage"]
            print("enemy damage player,current health  ", Player.health)

    if choice == "3":
        Player.defence += 1
        print("player goes into a defencive stance, increasing def to:", Player.defence)
        if random.randint(0, 100) <= Player.evade:
            print("enemy misses player")
        elif random.randint(0, 100) >= Player.evade:
            Player.health = Player.health + Player.defence - Enemy["damage"]
            print("enemy damage player,current health  ", Player.health)
        Player.defence -= 1

    if choice == "4":
        print(Player.player_status)

    if Enemy["health"] <= 0 or Player.health <= 0:
        if Enemy["health"] <= 0:
            print("player wins!!!  Congratulation")
        if Player.health <= 0:
            print("You have been slayed, Game over!!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
