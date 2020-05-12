---
title: python script Learn ClassTicTak (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Learn ClassTicTak'


Modules used in program: 
* `import random`

## python Learn ClassTicTak

Python mysql example: Learn ClassTicTak

```python
import random

class TikTakBoard(object):

    def __init__(self, size):
        self.size = size
        self.board = [['-'] * self.size] * self.size

    def __str__(self):
        str_print(= "")
        for row in self.board:
            str_print(+= "|")
            for column in row:
                str_print(+= column + "|")
            str_print(+= "\n")
        return str_print

    def reset_board(self):
        self.board.clear()
        self.board = [['-'] * self.size] * self.size

a = TikTakBoard(8)
print(a)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
