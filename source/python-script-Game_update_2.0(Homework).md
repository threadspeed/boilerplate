---
title: python script Game update 2.0(Homework) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Game update 2.0(Homework)'


Modules used in program: 
* `import random`

## python Game update 2.0(Homework)

Python example: Game update 2.0(Homework)

```python
import random
count = 5
score = 50
magic_number = random.randint(1,20)
while count>0:
    print('The chance left =',count)
    user_input=int(input('Enter Number Between 1 to 20: '))
    if user_input>20 or user_input<0:
        print('Sorry You Entered Wrong.')
        count -= 1
        continue
    calculator = abs(magic_number-user_input)
    if magic_number==user_input:
        print('Congratulation. He was at position=',magic_number)
        print('Score =',score)
        break
    elif calculator <= 2:
        print('So Close..')
        count -= 1
        score -= 10
    elif calculator <=4:
        print('Good try..')
        count -= 1
        score -= 10
    elif calculator <= 8:
        print('Ok,Out Of Luck...')
        count -= 1
        score -= 10
    elif calculator <= 12:
        print('Ummmmm, maybe a misfortune...')
        count -= 1
        score -= 10
    elif calculator <= 15:
        print('Your Luck Has expired..')
        count -= 1
        score -= 10
    else:
        print('Congratulation!! You Failed')
        count -= 1
        score -= 10
else:
    print('You Failed.. Better Luck Next Time')
input()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
