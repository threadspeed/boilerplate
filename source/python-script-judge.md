---
title: python script judge (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'judge'

Functions in program: 
* `def main():`

Modules used in program: 
* `import pandas as pd`
* `import numpy as np`
* `import random`

## python judge

Python example: judge

```python
import random

import numpy as np
import pandas as pd

from bot import Bot, RandomBot
from greedy import GreedyBot, LessGreedyBot, UpperLowerBot, KellyBot
from constants import *

def main():
    bot_classes = [Bot, RandomBot, GreedyBot, LessGreedyBot, UpperLowerBot, KellyBot]
    results = [[] for _ in range(len(bot_classes))]

    for round_number in range(N_ROUNDS):
        # Uniform(0, 1)
        # p = random.random()

        # Truncated normal
        p = np.random.normal(loc=0.5, scale=0.05)
        p = max(p, 0)
        p = min(p, 1)

        bots = [bot(STARTING_MONEY, N_TOSSES, ODDS) for bot in bot_classes]
        bot_money = [STARTING_MONEY for _ in range(len(bots))]

        for toss_number in range(N_TOSSES):
            toss_result = 'H' if random.random() < p else 'T'

            for bot_id, bot in enumerate(bots):
                resp = bot.next_action()

                if resp['action'] == 'skip':
                    continue

                elif resp['action'] == 'toss':
                    assert(resp['wager'] <= bot_money[bot_id])
                    bet_return = (ODDS - 1) * resp['wager'] if resp['side'] == toss_result else -1 * resp['wager']
                    bot.handle_toss(toss_result, bet_return)
                    bot_money[bot_id] += bet_return

                else:
                    print(f'Unknown action made by {str(bot)}')

        for bot_id, bot in enumerate(bots):
            results[bot_id].append(bot_money[bot_id])

    results_df = pd.DataFrame({'names':[str(bot(0, 0, 0)) for bot in bot_classes],
                               'average':[np.mean(scores) for scores in results],
                               'median':[np.median(scores) for scores in results],
                               '0.05':[np.quantile(scores, q=0.05) for scores in results],
                               '0.95':[np.quantile(scores, q=0.95) for scores in results],
                               'stddev':[np.std(scores) for scores in results]})

    print(results_df)


if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
