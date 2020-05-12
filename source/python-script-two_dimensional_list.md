---
title: python script two dimensional list (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'two dimensional list'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python two dimensional list

Python mysql example: two dimensional list

```python
# Okay I'll try once again
# Let's assign random numbers to
# a two dimensional list

# import random

import random

# Constants for rows and columns
ROWS = 3
COLS = 3
def main():
    # create a two- dimensional list
    # hay hay efendim

    values = [[0, 0, 0],
              [0, 0, 0],
              [0, 0, 0]]

    # fill the list with random numbers
    for r in range(ROWS):
        for c in range(COLS):
            values[r][c] = random.randint(1,900)

    # Display the random numbers
    print(values)

# call the function(main)
main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
