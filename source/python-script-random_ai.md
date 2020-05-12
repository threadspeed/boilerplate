---
title: python script random ai (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random ai'


Modules used in program: 
* `import random`

## python random ai

Python example: random ai

```python
""" Random AI """
import random
from player import Player

class RandomAIPlayer(Player):
    """ Returning random playable Cards """

    def _init(self):
        return 0

    def _choose_move(self):
        return random.choice(self.cards)

    def _game_over(self, won_lost_tie):
        return 0


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
