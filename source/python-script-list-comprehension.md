---
title: python script list-comprehension (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'list-comprehension'


## python list-comprehension

Python mysql example: list-comprehension

```python
# Create a list of list for the cells (LONG WAY):
nextCells = []
for x in range(WIDTH):
    column = [] # Create a new column
    for y in range(HEIGHT):
        if random.randint(0, 1) == 0:
            column.append('#') # Add a living cell.
        else:
            column.append(' ') #Add a dead cell.
    nextCells.append(column) # nextCells is a list of column lists. 
    
    
# Create a list of list for the cells (SHORT WAY):
cells = [['#' if random.randint(0, 1) == 0 else ' ' for y in range(HEIGHT)] for x in range(WIDTH)]

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
