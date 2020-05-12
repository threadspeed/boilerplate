---
title: python script cards (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cards'

Functions in program: 
* `def do_strategy(deck, score, cards_remaining, verbose):`
* `def calculate(current, total_remain, b_remain, r_remain):`

Modules used in program: 
* `import itertools`
* `import random`

## python cards

Python example: cards

```python
import random
import itertools

# solution is a dictionary:
#   - Key is a tuple of (score: int, cards_remaining: int)
#   - Value is a tuple of (continue_drawing: bool, expected_value: float)
solution = {
    (-1, 1): (True, 0),
    (1, 1): (False, 1)
}

# build up solution (dynamic programming)
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


COLORS = ['red', 'red', 'black', 'black']
RANKS = '23456789TJQKA'
DECK = tuple(card for card in itertools.product(RANKS, COLORS))
my_deck = random.sample(DECK, 52)

calculate(0, 52, 26, 26)
result = do_strategy(my_deck, 0, 52, True)
print(result)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
