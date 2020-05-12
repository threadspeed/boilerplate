---
title: python script kaggle learn py day1 11 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'kaggle learn py day1 11'


Modules used in program: 
* `import random`

## python kaggle learn py day1 11

Python example: kaggle learn py day1 11

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
rows = 3
cols = 5
# The height and width of the whole grid, measured in inches.
height = 5
width = 16

## Step 3: Create the grid
grid = plt.subplots(rows, cols, figsize=(width, height))

## Step 4: Draw the sketches in the grid
draw_images_on_subplots(imgs, grid)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
