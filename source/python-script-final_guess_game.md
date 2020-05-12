---
title: python script final guess game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'final guess game'


Modules used in program: 
* `import random`

## python final guess game

Python mysql example: final guess game

```python
import random
mf = random.randint(1, 20)
life = 5
while life > 0:
  guess = int(input('enter your guess: '))
  diff = abs(mg - guess)
  if not 0 < guess <= 20:
    print('invalid')
    continue
  elif diff is 0:
    print('congratulations! {}'.format(life*10))
    break
  elif diff <3:
    print('very close!')
  elif diff <5:
    print('near')
  else:
    print('too far')
  life -= 1   
else:
  print('you lose !')
  
  

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
