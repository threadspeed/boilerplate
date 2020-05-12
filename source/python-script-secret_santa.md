---
title: python script secret santa (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'secret santa'

Functions in program: 
* `def good_pair(ilegal_pair_list, giver, receiver):`
* `def pairwise(iterable):`
* `def main(seed, log):`

Modules used in program: 
* `import sys`
* `import logging`
* `import argparse`
* `import itertools`
* `import random`

## python secret santa

Python mysql example: secret santa

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import random
import itertools
import argparse
import logging
import sys


def main(seed, log):
    logging.basicConfig(level=getattr(logging, str(log).upper()))
    LOGGER = logging.getLogger(__name__)

    random.seed(seed)
    people_list = ['x', 'y', 'z', 'a', 'b', 'c']
    ilegal_pair_list = [['x', 'y'],['x', 'c']]

    LOGGER.debug('People=%s', people_list)
    LOGGER.debug('Ignore pairs=%s', ilegal_pair_list)

    # Ja lasa failu no stdin
    # people_list = [line.strip() for line in open(str(sys.argv[1]))]
    # ilegal_pair_list = [line.split() for line in open(str(sys.argv[2]))]

    result = []

    while people_list:
        chosen = random.choice(people_list)

        while result and not good_pair(ilegal_pair_list, chosen, result[-1]):
            chosen = random.choice(people_list)

        result.append(chosen)
        people_list.remove(chosen)

    for giver, receiver in pairwise(result + [result[0]]):
        print('{} dāvina dāvanu {}'.format(giver, receiver))


def pairwise(iterable):
    "s -> (s0,s1), (s1,s2), (s2, s3), ..."
    a, b = itertools.tee(iterable)
    next(b, None)
    return itertools.izip(a, b)


def good_pair(ilegal_pair_list, giver, receiver):
    for pair in ilegal_pair_list:
        if set([giver,  receiver]) == set(pair):
            return False

    return True


if __name__ == '__main__':
    parser = argparse.ArgumentParser(description='Secret Santa Generator')
    parser.add_argument('--log', type=str, default='info')
    parser.add_argument('--seed', type=int, default=1)
    args = parser.parse_args()

    sys.exit(main(args.seed, args.log))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
