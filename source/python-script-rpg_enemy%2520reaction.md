---
title: python script rpg enemy%2520reaction (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpg enemy%2520reaction'


Modules used in program: 
* `import random`

## python rpg enemy%2520reaction

Python example: rpg enemy%2520reaction

```python
#!/usr/bin/env python3
import random


enemy = {"name": "enemy", "health": 22, "damage": 2, "defence": 0, "evade": 10}

if enemy["health"] > 5:
    if random.randint(0, 100) == 0-10:
        print("the enemy hisses at the player in anger")
    if random.randint(0, 100) == 11-20:
        print("the enemy dances around the player, tauntingly")
    if random.randint(0, 100) == 21 - 40:
        print("the enemy points finger in an improper way")
    if random.randint(0, 100) == 41 - 80:
        print("the enemy is....OH my,  that is not something that will be described here...")
    if random.randint(0, 100) == 81 - 100:
        print("the enemy dislikes the player")
if enemy["health"] < 5:
    if random.randint(0, 100) == 0-65:
        print("the enemy is plea'ing for its life")
    if random.randint(0, 100) == 66-100:
        print("the enemy wish that it's mother was here")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
