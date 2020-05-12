---
title: python script combat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'combat'


Modules used in program: 
* `import random`

## python combat

Python example: combat

```python
import random


class Combat:
    dodge_limit = 6
    attack_limit = 6
    block_limit = 6
    run_limit = 6

    def dodge(self):
        roll = random.randint(1, self.dodge_limit)
        return roll > 3

    def attack(self):
        roll = random.randint(1, self.attack_limit)
        return roll > 3

    def block(self):
        roll = random.randint(1, self.block_limit)
        return roll > 4

    def run(self):
        roll = random.randint(1, self.run_limit)
        return roll > 1

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
