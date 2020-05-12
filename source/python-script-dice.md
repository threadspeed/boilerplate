---
title: python script dice (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dice'

Functions in program: 
* `def main():`
* `def handleUserInput(string):`

Modules used in program: 
* `import re`
* `import sys`
* `import time`
* `import random`

## python dice

Python example: dice

```python
#!/usr/bin/python3
"""Write a nice and descriptive docstring."""
 
import random
import time
import sys
import re
 
# Define cpu clock as the random seed.
random.seed(time.clock)
random = random.randrange
 
# Create a dictionary for the dice.
dice = {"d4":   {"Start": 1, "End": 4, "Step": 1, "Times": 1},
        "d6":   {"Start": 1, "End": 6, "Step": 1, "Times": 1},
        "d8":   {"Start": 1, "End": 8, "Step": 1, "Times": 1},
        "d10":  {"Start": 1, "End": 10, "Step": 1, "Times": 1},
        "d12":  {"Start": 1, "End": 12, "Step": 1, "Times": 1},
        "d20":  {"Start": 1, "End": 20, "Step": 1, "Times": 1},
        "d100": {"Start": 1, "End": 100, "Step": 1, "Times": 1},
        "dX":   {"Start": 1, "End": 100, "Step": 1, "Times": 1},
 
# Set the default die (d6).
defaultDie = dice["d6"]
 
def handleUserInput(string):
    """Handles whatever input user gives."""
    string = string.lower()

    defaultPattern = re.compile("default d")

    if string == "exit" or string == "quit":
        # Quit the program.
        pass

    elif string == "help":
        # Print a help for the user.
        pass

    elif "default" in string:
        # Set the default dice.
        pass

    # Set the current die.
    currentDie = dice["d6"]
     
    # Get configuration from the current die.
    config = {"Start": currentDie[0],
              "End": currentDie[1],
              "Step": currentDie[2],
              "Times": currentDie[3]}

    print(config)
 
def main():
    """Runs the program."""
    while True:
        handleUserInput(input(">> "))

main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
