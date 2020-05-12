---
title: python script practicepython ex13 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex13'

Functions in program: 
* `def det_fib(maxcount):`
* `def get_interger(prompt="Please enter a number: "):`

## python practicepython ex13

Python mysql example: practicepython ex13

```python
#!/usr/bin/python


def get_interger(prompt="Please enter a number: "):
  return int(input(prompt))

def det_fib(maxcount):
  a = [ 1 ]
  if maxcount == 1:
    return a
  a.append(1)
  while len(a) < maxcount:
    a.append(a[-1]+a[-2])
  else:
    return a
  

print(det_fib(get_interger("How many Fibonnaci numbers would you like? ")))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
