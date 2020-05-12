---
title: python script 247combo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '247combo'

Functions in program: 
* `def times_to_cdf(times):`

Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import random`

## python 247combo

Python example: 247combo

```python
import random
import matplotlib.pyplot as plt
import numpy as np

random.seed(247)

jh = "Jackson"
ps = "Power Shutdown"
ad = "Accelerated Diagnostics"

num_trials = 100000

def times_to_cdf(times):
    num_below = map(lambda i: len(filter(lambda n: n <= i,
                                         times)),
                    range(49))
    return np.array(num_below) / float(max(num_below))



results = {}
for num_AD in [2, 3]:
    time_to_draw_1 = []
    time_to_draw_2 = []
    for _ in range(num_trials):
        deck = [jh]*3 + [ps]*2 + [ad]*num_AD
        deck += [None] * (49 - len(deck))
        hand = []
        random.shuffle(deck)
        
        while not (jh in hand and ps in hand and ad in hand):
            hand.append(deck.pop())
        time_to_draw_1.append(len(hand))

        hand.remove(ad)
        while not (jh in hand and ps in hand and ad in hand):
            hand.append(deck.pop())
        time_to_draw_2.append(len(hand))

        
    avg_to_draw_1 = sum(time_to_draw_1)/float(num_trials)
    avg_to_draw_2 = sum(time_to_draw_2)/float(num_trials)
    
    print("\navg to draw combo with {} ADs: {}".format(num_AD, avg_to_draw_1))
    print("avg to draw combo + extra AD with {} ADs: {}".format(num_AD, avg_to_draw_2))

    for num_drawn, times in [(1, time_to_draw_1), (2, time_to_draw_2)]:
        num_below = times_to_cdf(times)
        lbl = ("prob. of drawing combo{}"
               " with {} ADs in deck").format(" with extra AD"
                                              if num_drawn == 2 else "",
                                              num_AD)
        plt.plot(range(49), num_below, label=lbl)

    results[(num_AD, 1)] = times_to_cdf(time_to_draw_1)
    results[(num_AD, 2)] = times_to_cdf(time_to_draw_2)


diff_1 = results[(3, 1)] - results[(2, 1)]
diff_2 = results[(3, 2)] - results[(2, 2)]

    
plt.xlabel("Cards drawn")
plt.ylabel("Probability")
plt.legend(loc="upper left")
plt.show()

plt.xlabel("Cards drawn")
plt.ylabel("Probability")
plt.title("Chance of having drawn combo with 3 ADs, but not with 2 ADs")
plt.plot(range(49), diff_1, label="without extra AD")
plt.plot(range(49), diff_2, label="with extra AD")
plt.legend()
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
