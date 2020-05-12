---
title: python script MemoryGame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MemoryGame'

Functions in program: 
* `def play(difficulty):`
* `def is_list_equal(list_a, list_b):`
* `def set_user_number(index):`
* `def get_list_from_user(difficulty):`
* `def generate_sequence(difficulty):`

Modules used in program: 
* `import Utils`
* `import random`

## python MemoryGame

Python example: MemoryGame

```python
import random
import Utils


def generate_sequence(difficulty):
    numbers = []
    for i in range(difficulty):
        numbers.append(random.randint(1, 101))
    Utils.print_and_clean(numbers)
    return numbers


def get_list_from_user(difficulty):
    user_list = []
    print('After seeing the numbers enter the numbers you saw, each one separated with Enter.')
    for i in range(difficulty):
        user_list.append(set_user_number(i))

    return user_list


def set_user_number(index):
    user_input = input('please enter the number in index ' + str(index) + ': ')
    if user_input.isnumeric():
        return int(user_input)
    else:
        print('enter only numbers!')
        set_user_number(index)


def is_list_equal(list_a, list_b):
    index = int(len(list_a))
    for i in range(index):
        if list_a[i] == list_b[i]:
            continue
        else:
            return False
    return True


def play(difficulty):
    random_list = generate_sequence(difficulty)
    user_list = get_list_from_user(difficulty)
    return is_list_equal(random_list,user_list)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
