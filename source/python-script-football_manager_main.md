---
title: python script football manager main (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'football manager main'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python football manager main

Python mysql example: football manager main

```python
import random

from team import League, Team
from player import generate_player


def main():
    # set up our data
    # generate some players
    players = list()
    for i in range(100):
        players.append(generate_player())

    # five teams setting
    teams = [
        Team('Lech'),
        Team('Legia'),
        Team('Cracovia'),
        Team('Wisła'),
        Team('Wisła Płock'),
    ]

    for team in teams:
        for player_num in range(11):
            # give them 11 staring players
            selected_players = random.choice(players)
            team.players.append(selected_players)
            players.remove(selected_players)

    # we have a single league
    first_league = League("Ekstraklasa")
    first_league.set_teams(teams)

    first_league.play_season(10)


if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
