---
title: python script c135 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'c135'


## python c135

Python example: c135

```python
'''a, b = map(int, input().split()); p = __builtins__.print
while 1:
    eq = ''.join(list(__import__('itertools').chain(*zip(["{}".format(__import__('random').randint(a, b)) for i in range(4)], list(sorted(['+', '-', '*'], key=lambda *args: __import__('random').random()))))) + ["{}".format(__import__('random').randint(a, b))])
    p("> {}".format(eq))
    while 1:
        _ = input()
        if _ == "{}".format(eval(eq)): p("welldone");break
        elif _ == "q": exit(p("quitting"))
        else: p("tryagain")


'''
from itertools import chain
from random import shuffle, randint

a, b = map(int, input().split())

op = ['+', '-', '*']

while 1:
    #generate the numbers for the problem
    #str because chain wants it
    nums = [str(randint(a, b)) for i in range(4)]
    #shuffle the ops
    shuffle(op)

    #chain between zipped nums and op
    #NUM1 OP1 NUM2 OP2 NUM3 OP3 + NUM4 (+NUM 4 because it cuts the last number)
    eq = ''.join(list(chain(*zip(nums, op))) + [nums[-1]])
    result = str(eval(eq))
    
    print("> {}".format(eq))
    while 1:
        answer = input()
        if answer == result:
            print("welldone")
            break
        elif answer == 'q':
            exit(print("quitting"))
        else:
            print("tryagain")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
