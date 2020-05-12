---
title: python script puzzle (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'puzzle'

Functions in program: 
* `def can_construct(soup, message):`
* `def get_soup(letters):`
* `def _get_random_gen(max):`
* `def _get_random_letter():`

Modules used in program: 
* `import time`
* `import random`
* `import string`

## python puzzle

Python example: puzzle

```python
import string
import random
import time
from collections import Counter


def _get_random_letter():
    """
    Returns a random char from ASCII_UPPERCASE
    :return: Random char
    """
    return random.choice(string.ascii_uppercase)


def _get_random_gen(max):
    """
    Creates a generator with random letters that represents the alphabet soup
    :param max: number of letters
    :return: Generator containing all the letters
    """
    for _ in range(max):
        yield _get_random_letter()


def get_soup(letters):
    """
    Returns  a Counter with all the letters contained in the soup and the number
    :param letters:
    :return: Counter
    """
    return Counter(_get_random_gen(letters))


def can_construct(soup, message):
    """
    This function determines if a message can be written with the letters
    contained in a letter soup

    :param soup: Generator that represents the letters contained in the soup
    :param message:  String containing the message
    :return: True if message can be written. False otherwise
    """
    for letter in message.replace(" ", ""):
        if soup[letter] > 0:
            soup[letter] -= 1
        else:
            return False
    return True


if __name__ == "__main__":
    gen = get_soup(500000)
    start_time = time.time()
    print(can_construct(gen, "THIS IS MY SOLUTION TO THE PUZZLE"))
    print("--- %s seconds ---" % (time.time() - start_time))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
