---
title: python script schedule examples (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'schedule examples'

Functions in program: 
* `def test_function_2():`
* `def test_function():`

Modules used in program: 
* `import schedule`
* `import time`

## python schedule examples

Python example: schedule examples

```python
import time
import schedule

def test_function():
    print(f'test called at {time.time()}')

def test_function_2():
    print(f'test 2 called at {time.time()}')

if __name__ == '__main__':
    schedule.every(1).seconds.do(test_function)
    schedule.every(3).seconds.do(test_function_2)
    # schedule.every(1).days.do(daily_task)
    # schedule.every().thursday.at("10:00").do(day_time_task)

    while True:
        schedule.run_pending()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
