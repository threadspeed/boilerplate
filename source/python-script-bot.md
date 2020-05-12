---
title: python script bot (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bot'


Modules used in program: 
* `import random`

## python bot

Python example: bot

```python
import random

class Bot():
    def __init__(self, money, n_tosses, odds):
        self.money = money
        self.n_tosses = n_tosses
        self.odds = odds

    def handle_toss(self, toss_result, bet_return):
        pass

    def next_action(self):
        return {'action':'skip'}

    def __repr__(self):
        return 'Bot'

class RandomBot(Bot):
    """
    RandomBot randomly chooses a side to flip for each time. It will flip
    up to `max_tosses` times, betting `wager` each time.
    """
    def __init__(self, money, n_tosses, odds):
        super().__init__(money, n_tosses, odds)
        self.max_tosses = 10
        self.played_tosses = 0
        self.wager = 5

    def __repr__(self):
        return 'RandomBot'

    def handle_toss(self, toss_result, bet_return):
        # Update money and number of tosses
        self.money += bet_return
        self.played_tosses += 1

    def next_action(self):
        # Quit if we've played enough games
        if self.played_tosses >= self.max_tosses:
            return {'action':'skip'}

        # Toss a random side
        side = random.choice(['H', 'T'])
        return {'action':'toss', 'side':side, 'wager':self.wager}


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
