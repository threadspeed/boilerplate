---
title: python script kaggle learn py day1 12 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'kaggle learn py day1 12'


Modules used in program: 
* `import random`

## python kaggle learn py day1 12

Python example: kaggle learn py day1 12

```python
import random
from matplotlib import pyplot as plt
from learntools.python.quickdraw import random_category, sample_images_of_category, draw_images_on_subplots

## Step 1: Sample some sketches
# How many sketches to view - a random number from 2 to 20
n = random.randint(2, 20)
# Choose a random quickdraw category. (Check out https://quickdraw.withgoogle.com/data for an overview of categories)
category = random_category()
imgs = sample_images_of_category(n, category)

## Step 2: Choose the grid properties
######## Your changes should go here ###############
rows = int(round(n / 8 + 1))
cols = min(n // rows + 1, n)
# The height and width of the whole grid, measured in inches.
height = rows * 2
width = cols * 2

## Step 3: Create the grid
grid = plt.subplots(rows, cols, figsize=(width, height))

## Step 4: Draw the sketches in the grid
draw_images_on_subplots(imgs, grid)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
