---
title: python script cards2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cards2'

Functions in program: 
* `def run_mo(deck):`
* `def choice(deck):`
* `def calc_eval(deck: np.ndarray):`
* `def do_strategy(deck, score, cards_remaining, verbose):`
* `def calculate(current, total_remain, b_remain, r_remain):`

Modules used in program: 
* `import statistics`
* `import numpy as np`
* `import functools`
* `import itertools`
* `import random`

## python cards2

Python mysql example: cards2

```python
import random
import itertools
import functools
import numpy as np

solution = {
    (-1, 1): (True, 0),
    (1, 1): (False, 1)
}


def calculate(current, total_remain, b_remain, r_remain):
    if (current, total_remain) not in solution:
        if b_remain == 0 or total_remain == 0:
            solution[(current, total_remain)] = (False, current)
        else:
            b_ev = calculate(current + 1, total_remain - 1, b_remain - 1, r_remain)
            r_ev = calculate(current - 1, total_remain - 1, b_remain, r_remain - 1)
            b_pct = b_remain / total_remain
            r_pct = r_remain / total_remain
            ev_draw = (b_ev * b_pct) + (r_ev * r_pct)
            do_draw = ev_draw > current
            ev = ev_draw if do_draw else current
            solution[(current, total_remain)] = (do_draw, ev)

    return solution[(current, total_remain)][1]


def do_strategy(deck, score, cards_remaining, verbose):
    if cards_remaining <= 0:
        return 0

    next_step = solution[(score, cards_remaining)]
    if verbose:
        print('{0}: {1}'.format((score, cards_remaining), next_step))
    if next_step[0]:
        card = deck[-1 * cards_remaining]
        new_score = score + 1 if card[1] == 'black' else score - 1
        return do_strategy(deck, new_score, cards_remaining - 1, verbose)
    else:
        return score


SIM_LENGTH = 1000


def calc_eval(deck: np.ndarray):
    total = 0
    vector = np.array(deck.copy())
    for i in range(SIM_LENGTH):
        np.random.shuffle(vector)
        total += vector.cumsum().max()
    return total / SIM_LENGTH


def choice(deck):
    return calc_eval(deck) > 0


def run_mo(deck):
    total = 0
    for i in range(52):
        c = choice(deck[i:])
        if c:
            total += deck[i]
        else:
            return total
    return total

COLORS = ['red', 'red', 'black', 'black']
RANKS = '23456789TJQKA'
DECK = tuple(card for card in itertools.product(RANKS, COLORS))
calculate(0, 52, 26, 26)

results = []
for i in range(100):
    my_deck = random.sample(DECK, 52)
    mod_deck = [1 if t[1] == 'black' else -1 for t in my_deck]

    result = do_strategy(my_deck, 0, 52, False)
    mo_result = run_mo(mod_deck)
    results.append((result, mo_result))

import statistics
mean = statistics.mean([r[0] for r in results])
mo_mean = statistics.mean([r[1] for r in results])

outperforms = len([r for r in results if r[0] > r[1]])
ties = len([r for r in results if r[0] == r[1]])
mo_outperforms = len([r for r in results if r[0] < r[1]])

# print(result)
# print('mo_result {0}'.format(mo_result))




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
