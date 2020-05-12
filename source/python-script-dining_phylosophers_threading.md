---
title: python script dining phylosophers threading (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dining phylosophers threading'

Functions in program: 
* `def philosopher(n):`
* `def sleep():`

Modules used in program: 
* `import threading`
* `import random`
* `import time`

## python dining phylosophers threading

Python example: dining phylosophers threading

```python
import time
import random
import threading

def sleep():
    time.sleep(random.random())

N = 5
sticks = [threading.Lock() for n in range(N)]

def philosopher(n):
    sleep()
    with sticks[n]:
        sleep()
        with sticks[(n+1)%N]:
            sleep()
            print(f'Philosopher {n} eating')
            sleep()


tasks = [threading.Thread(target=philosopher, args=(i,)) for i in range(N)]
[task.start() for task in tasks]
[task.join() for task in tasks]


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
