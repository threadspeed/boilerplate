---
title: python script StrategyTester (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'StrategyTester'

Functions in program: 
* `def wins_to_cumulative_probability(wins, num_of_games):`
* `def test_strategy(strategy, num_of_games):`

Modules used in program: 
* `import Warships as WS`
* `import random`

## python StrategyTester

Python mysql example: StrategyTester

```python
import random
import Warships as WS
from Warships import Point


def test_strategy(strategy, num_of_games):
    wins = [0 for i in range(101)]

    for i in range(num_of_games):
        grid = WS.gen_rand_grid()
        while not grid.is_won():
            strategy(grid)
        wins[grid.checked_cells] += 1
        print("Won {} game out of {} games".format(i + 1, num_of_games))
    probabilities = wins_to_cumulative_probability(wins, num_of_games)
    print("List of wins:")
    print(wins)
    print("List of cumulative probabilities of winning at some number of moves:")
    print(probabilities)


def wins_to_cumulative_probability(wins, num_of_games):
    probability = []
    current_probability = 0
    for item in wins:
        if item != 0:
            current_probability += item / num_of_games
        probability.append(current_probability)
    return probability


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
