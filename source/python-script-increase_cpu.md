---
title: python script increase cpu (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'increase cpu'

Functions in program: 
* `def main():`
* `def work(t):`

Modules used in program: 
* `import random`

## python increase cpu

Python example: increase cpu

```python
#!/usr/bin/env python3

from argparse import ArgumentParser
from datetime import datetime, timedelta
from multiprocessing import Process
import random

def work(t):
    current_time = datetime.now()
    delta = timedelta(seconds=t)
    exit_time = current_time + delta
    while datetime.now() <= exit_time:
        res = random.randint(2, 10)
        for i in range(1000000):
            res *= random.randint(2, 10)
            res /= random.randint(2, 10)

def main():
    parser = ArgumentParser()
    parser.add_argument("-p", "--process",
            type=int, help="Number of processes", required=True)
    parser.add_argument("-t", "--time",
            type=int, help="Running time in seconds", required=True)
    args = parser.parse_args()

    all_processes = [Process(target=work, args=(args.time,)) for i in range(args.process)]
    print("Starting...")
    for p in all_processes:
        p.start()
    for p in all_processes:
        p.join()
    print("Complete!")

if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
