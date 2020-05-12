---
title: python script lotery (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lotery'

Functions in program: 
* `def main():`
* `def generate_lottery_numbers(quantity):`

Modules used in program: 
* `import random`

## python lotery

Python mysql example: lotery

```python
import random

def generate_lottery_numbers(quantity):
    num_list = []

    while True:
        if len(num_list) == quantity:
            break

        lot_num = random.randint(1, 100)

        if lot_num not in num_list:
            num_list.append(lot_num)

    return num_list

def main():
    print("Welcome to the Lottery numbers generator !")

    quantity_question = raw_input("Please enter how many random numbers would you like to have: ")

    try:
        quantity_num = int(quantity_question)
        print(generate_lottery_numbers(quantity_num))
    except ValueError:
        print("Please enter a number.")

    print("END.")

if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
