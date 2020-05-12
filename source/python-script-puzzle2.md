---
title: python script puzzle2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'puzzle2'

Functions in program: 
* `def can_construct(soup, message):`
* `def _update_message(letter, message):`
* `def get_random_gen(max):`
* `def _get_random_letter():`

Modules used in program: 
* `import time`
* `import random`
* `import string`

## python puzzle2

Python mysql example: puzzle2

```python
import string
import random
import time


def _get_random_letter():
    """
    Returns a random char from ASCII_UPPERCASE
    :return: Random char
    """
    return random.choice(string.ascii_uppercase)


def get_random_gen(max):
    """
    Creates a generator with random letters that represents the alphabet soup
    :param max: number of letters
    :return: Generator containing all the letters
    """
    for _ in range(max):
        yield _get_random_letter()


def _update_message(letter, message):
    """
    This function marks the found letters in the message
    :param letter: Current letter
    :param message: Message
    :return: True if the letter was found in the message. False otherwise
    """
    try:
        message.pop(message.index(letter))
        return True
    except ValueError:
        return False


def can_construct(soup, message):
    """
    This function determines if a message can be written with the letters
    contained in a letter soup

    :param soup: Generator that represents the letters contained in the soup
    :param message:  String containing the message
    :return: True if message can be written. False otherwise
    """
    can = False
    message_list = list(message.replace(" ", ""))

    for i in soup:
        if len(message_list) > 0:
            _update_message(i, message_list)
        else:
            can = True
            break
    return can


if __name__ == "__main__":
    gen = get_random_gen(500000)
    start_time = time.time()
    print(can_construct(gen, "THIS IS MY SOLUTION TO THE PUZZLE"))
    print("--- %s seconds ---" % (time.time() - start_time))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
