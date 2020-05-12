---
title: python script dining phylosophers thredo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dining phylosophers thredo'

Functions in program: 
* `def main():`
* `def philosopher(n):`
* `def sleep():`

Modules used in program: 
* `import thredo`
* `import random`

## python dining phylosophers thredo

Python mysql example: dining phylosophers thredo

```python
import random
import thredo

def sleep():
    thredo.sleep(random.random())

N = 5
sticks = [thredo.Lock() for n in range(N)]

def philosopher(n):
    sleep()
    with sticks[n]:
        sleep()
        with sticks[(n+1)%N]:
            sleep()
            print(f'Philosopher {n} eating')
            sleep()

def main():
    tasks = [thredo.spawn(philosopher, i) for i in range(N)]
    [task.wait() for task in tasks]

thredo.run(main)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
