---
title: python script find first (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'find first'

Functions in program: 
* `def find_first_naive(string):`
* `def find_first(string):`

Modules used in program: 
* `import random`
* `import string`

## python find first

Python mysql example: find first

```python
import string
import random
from collections import defaultdict

def find_first(string):
    print(string)
    if not string:
        return 0
    counts = defaultdict(int)
    for letter in list(string):
        counts[letter] += 1
    counts = {k:v for k, v in counts.items() if v == 1}
    for letter in list(string):
        if letter in counts.keys():
            print(letter)
            return letter
    return 0

def find_first_naive(string):
    for letter in string:
        if string.count(letter) == 1:
            return letter
    return 0


if __name__ == "__main__":
    test_times = int(input("How many times to test? "))
    test_length = int(input("Insert test length: "))
    for i in range(test_times):
        test_case = ""
        random.seed(a=None)
        for y in range(test_length):
            test_case = f"{test_case}{string.ascii_lowercase[random.randint(0, 25)]}"
        if find_first(test_case) == find_first_naive(test_case):
            print("OK")
        else:
            print(f"Error, returned {find_first(test_case)}, naive returned {find_first_naive(test_case)}")
            print(f"Data set: {test_case}")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
