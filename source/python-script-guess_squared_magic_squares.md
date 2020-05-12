---
title: python script guess squared magic squares (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guess squared magic squares'

Functions in program: 
* `def main():`
* `def compute_squared_set(squared_set, square_sets_per_thread_proc):`

Modules used in program: 
* `import lox`
* `import time`
* `import random`

## python guess squared magic squares

Python example: guess squared magic squares

```python
import random
import time
import lox

@lox.process(10)
def compute_squared_set(squared_set, square_sets_per_thread_proc):
    import random
    def compute_square(numbers):
        "For each row, column, and diagonal check that they all sum to the same number"
        magic = sum(numbers[:3])
        if sum(numbers[3:6]) != magic:
            return False
        if sum(numbers[6:]) != magic:
            return False
        if sum(numbers[::3]) != magic:
            return False
        if sum(numbers[1::3]) != magic:
            return False
        if sum(numbers[2::3]) != magic:
            return False
        if sum(numbers[::4]) != magic:
            return False
        if sum(numbers[2:7:2]) != magic:
            return False
        return True
    random.shuffle(squared_set)
    for _ in range(square_sets_per_thread_proc):
        for index in range(90):
            if compute_square(squared_set[index:index+9]):
                return squared_set[index:index+9]
    return False

SQUARE_SETS_PER_THREAD_PROC = 100000
THREAD_PROC_COUNT = 5
            
def main():
    start_time = time.perf_counter()
    all_squared_numbers = [x**x for x in range(100)]
    for i in range(THREAD_PROC_COUNT):
        random.shuffle(all_squared_numbers)
        compute_squared_set.scatter(all_squared_numbers,SQUARE_SETS_PER_THREAD_PROC)
    results = compute_squared_set.gather()
    if any(results):
        print(results)
    duration = time.perf_counter() - start_time
    completed_squares = SQUARE_SETS_PER_THREAD_PROC * THREAD_PROC_COUNT * 90
    print(f"{completed_squares/duration:,} tries per second over {duration} seconds")


if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
