---
title: python script GuessingGame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GuessingGame'


Modules used in program: 
* `import random`

## python GuessingGame

Python mysql example: GuessingGame

```python
import random
secretnumb=random.randint(1,10)

answer=int(input("What's the number I'm thinking of? "))

while answer!=secretnumb:    
    if answer>secretnumb:
        print("that number is too high")
        
    elif answer<secretnumb:
        print("that number is too low")
        
    else:
        print("That's the number!")

    answer=int(input("What's the number I'm thinking of? "))    

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
