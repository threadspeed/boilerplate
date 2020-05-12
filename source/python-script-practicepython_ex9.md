---
title: python script practicepython ex9 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex9'


Modules used in program: 
* `import random`

## python practicepython ex9

Python mysql example: practicepython ex9

```python
#!/usr/bin/python

import random
random.seed()
rand = random.randint(1,9)
guess = 1

while True:

  num = raw_input("(guess " + str(guess) + ") Guess a number between 1 and 9 (type exit to quit): ")

  if num == "exit":
    print("The number was " + rand + ".")
    break
  elif int(num) == rand:
    print("That is correct!  It took you " + str(guess) + " guess(es).")
    break
  elif int(num) < rand:
    print("Your number is too low.")
  else:
    print("Your number is too high.")

  guess+=1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
