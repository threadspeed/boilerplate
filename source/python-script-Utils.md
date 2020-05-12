---
title: python script Utils (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Utils'

Functions in program: 
* `def ERROR_MESSAGE():`
* `def SCORES_FILE_NAME():`
* `def clear():`
* `def print_and_clean(array):`

Modules used in program: 
* `import time`
* `import os`

## python Utils

Python example: Utils

```python
import os
import time


def print_and_clean(array):
    print(array)
    time.sleep(0.7)
    clear()


# I've not found a way to os.system("clear") in mac os so there is an workaround
def clear():
    print("\n" * 100)


def SCORES_FILE_NAME():
    return './Scores.txt'


def ERROR_MESSAGE():
    return 'Something went wrong..'


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
