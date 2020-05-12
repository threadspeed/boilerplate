---
title: python script rpg hitrate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rpg hitrate'


Modules used in program: 
* `import random`

## python rpg hitrate

Python mysql example: rpg hitrate

```python
#!/usr/bin/env python3
import random

"""
hit_rate system
"""

if random.randint(0, 100) <= player["evade"]:
    print("miss")
if random.randint(0, 100) >= player["evade"]:
    print("hit")
if random.randint(0, 100) == player["evade"]:
    print("grazed")
if random.randint(0, 100) == 0:
    print("critical fail")
if random.randint(0, 100) <= player["critical"]:
    print("critical hit")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
