---
title: python script week 007 timer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 007 timer'

Functions in program: 
* `def timer(seconds = 0, minutes = 0, hours = 0):`
* `def print_time(seconds, minutes, hours):`
* `def t(m):`

## python week 007 timer

Python example: week 007 timer

```python
def t(m):
    return "%02d" % (m)

def print_time(seconds, minutes, hours):
    print("%s:%s:%s" % (t(hours), t(minutes), t(seconds)))

def timer(seconds = 0, minutes = 0, hours = 0):
    if seconds >= 60:
        hours += seconds // 3600
        minutes += (seconds - hours * 3600) // 60
        seconds -= (hours * 3600 + minutes * 60)
    if hours < 100:
        for i_hrs in range(hours, -1, -1):
            for i_mins in range(minutes, -1, -1):
                for i_secs in range(seconds, -1, -1):
                    print_time(i_secs, i_mins, i_hrs)
                seconds = 59
            minutes = 59
    else:
        print("Error. The number of hours cannot be greater than 99.")
    

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
