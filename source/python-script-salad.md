---
title: python script salad (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'salad'

Functions in program: 
* `def main():`
* `def display_salad(dressing, ingredients):`
* `def combine_ingredients(leaf, fruits, nuts):`

Modules used in program: 
* `import random`

## python salad

Python mysql example: salad

```python
import random

leaf = 'spinach'
dressing = 'italian'
fruits = ['apple', 'orange']
nuts = ['almond', 'sunflower_seed']


def combine_ingredients(leaf, fruits, nuts):
    ingredients = [leaf]

    for fruit in fruits:
        ingredients.append(fruit)

    for nut in nuts:
        ingredients.append(nut)

    return ingredients


def display_salad(dressing, ingredients):
    print('Here comes your salad!')
    print('It has the following ingredients to be topped with {} dressing:'.format(dressing))
    for ingredient in ingredients:
        print('- {}'.format(ingredient))


def main():
    # Get the ingredients
    ingredients = combine_ingredients(leaf, fruits, nuts)

    # Shuffle the ingredients
    random.shuffle(ingredients)

    # Print the salad to the screen
    display_salad(dressing, ingredients)


main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
