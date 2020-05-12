---
title: python script magic numbers (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'magic numbers'


Modules used in program: 
* `import random`

## python magic numbers

Python mysql example: magic numbers

```python
import random

magic_numbers = [random.randint(0,9), random.randint(0,9)]

#print(magic_numbers)

chances = 3
input_usernumber_message = "This is attempt {}. Enter a number between 0 and 9: "

for attempt in range(chances): # based on initial value, it can be [0,1,2]
    user_number = int(input(input_usernumber_message.format(attempt + 1)))
    if user_number in magic_numbers:
        print(">>>>> You got the number right! <<<<<")
    else:
        print("..You didn't quite get it")



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
