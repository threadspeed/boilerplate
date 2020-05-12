---
title: python script football manager player (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'football manager player'

Functions in program: 
* `def generate_player():`

Modules used in program: 
* `import random`

## python football manager player

Python example: football manager player

```python
import random


class Player:
    """
    player is on a single team, with other players
    player plays in a game for a team
    """

    def __init__(self, name, skill):
        self.name = name

        # player skills rankings
        self.skill = skill

        # salary
        pass

    def salary(self):
        return 50000 + self.skill * 100


def generate_player():
    first_names = [
        "Noah",
        "Liam",
        "Mason",
        "Elijah",
        "Michael",
        "Aiden",
        "Jacob",
        "James",
        "Matthew",
        "William",
        "Josiah",
        "Grayson",
        "Luke",
        "Jaxon",
        "Andrew",
        "Isaiah",
        "Ryan",

        "Owen",
        "Isaac",
        "John",
    ]

    first_name = random.choice(first_names)
    last_names = random.choice(first_names)

    full_name = "{} {}".format(first_name, last_names)

    skill = 10 + random.randint(0, 90)

    return Player('name', skill)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
