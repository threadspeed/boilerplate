---
title: python script increase memory (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'increase memory'

Functions in program: 
* `def main():`
* `def task(s, t, i):`
* `def use(res):`
* `def generate_numbers(s):`

Modules used in program: 
* `import time`
* `import random`

## python increase memory

Python example: increase memory

```python
#!/usr/bin/env python3

from argparse import ArgumentParser
from datetime import datetime, timedelta
from multiprocessing import Process
import random
import time

def generate_numbers(s):
    num = random.randint(20000, 1000000)
    res = [[[num for k in range(1000)] for j in range(1000)] for i in range(s)]
    return res

def use(res):
    i = len(res)
    j = len(res[0])
    k = len(res[0][0])
    ans = 0
    for z in range(10):
        ans += res[random.randrange(0, i)][random.randrange(0, j)][random.randrange(0, k)] * \
                res[random.randrange(0, i)][random.randrange(0, j)][random.randrange(0, k)]

def task(s, t, i):
    print("Process", i, "loading data...")
    res = generate_numbers(s)
    print("Process", i, "loading complete.")
    current_time = datetime.now()
    delta = timedelta(seconds=t)
    exit_time = current_time + delta
    while datetime.now() <= exit_time:
        use(res)
        time.sleep(0.1)
    print("Process", i, "exit.")

def main():
    parser = ArgumentParser()
    parser.add_argument("-s", "--size",
            type=int, help="Number of integers in million", required=True)
    parser.add_argument("-p", "--process",
            type=int, help="Number of processes", required=True)
    parser.add_argument("-t", "--time",
            type=int, help="Running time in seconds", required=True)
    args = parser.parse_args()

    all_processes = [Process(target=task, args=(args.size, args.time, i)) for i in range(args.process)]
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
