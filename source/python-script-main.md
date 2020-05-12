---
title: python script main (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'main'


## python main

Python example: main

```python
""" Let the Game begin """
from random_ai import RandomAIPlayer
from real_player import RealPlayer
from game import Game

p1 = RealPlayer("Niko")

p2 = RandomAIPlayer ("John")
p3 = RandomAIPlayer ("Peter")

g = Game()
g.init_game(p1, p3, verbose=True)
for i in range(1):
    g.start_new_match()

print(p1.won_games)
print(p3.won_games)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
