---
title: python script binary lotto v2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'binary lotto v2'


Modules used in program: 
* `import random`

## python binary lotto v2

Python mysql example: binary lotto v2

```python
# Ask the user to enter two numbers between 0 - 1, 
# if the user gets all numbers correct then print(the message: "Yay!, you are a winner!", if not "Try Again!")
#
# 1. Ask the user for 2 numbers
# 2. Store the numbers in a list called "winning_numbers"
# 3. Create a list of two numbers: 0 and 1 called "choices"
# 4. Store two numbers in a list called "numbers" each number in the list must use the random.choice([0, 1]) method
# 5. Determine if both lists are equal and print(the appropriate message)
#
# Hint:
# At the very top of your code add include the random module:
# import random
# Use "choice" the method of the random module, to randomly select a value from the list
# random.choice([0, 1])


import random

num1 = int(input("Enter a number: "))
num2 = int(input("Enter a number: "))

numbers = [num1, num2]
winning_numbers = [random.choice([0, 1]), random.choice([0, 1])]

if winning_numbers == numbers:
  print("Yay!, you are a winner!")
else:
  print("Try Again!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
