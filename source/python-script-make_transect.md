---
title: python script make transect (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'make transect'

Functions in program: 
* `def make_transect():`
* `def print_transect(x_cord, y_cord):`
* `def make_coordinates(x_pos, y_pos):`
* `def make_y_pos():`
* `def make_x_pos(n=4):`

## python make transect

Python mysql example: make transect

```python


def make_x_pos(n=4):
    import random
    '''Creates n sample locations '''

    a = random.sample(range(1, 9), n)

    # test that 2 values are less than or equal to 5:
    if sum([x < 5 for x in a]) == 2:
        a.sort()
        return a
    else:
        return make_x_pos()


def make_y_pos():
    import random

    a = random.sample(range(-4, 4), 2)

    # test that 1 value is less than or equal to 0:
    if sum([x <= 0 for x in a]) == 1:
        return a
    else:
        return make_y_pos()


def make_coordinates(x_pos, y_pos):

    x_cord = []
    y_cord = []
    [x_cord.extend([x * 10]) for x in x_pos]
    [y_cord.extend([x * 10]) for x in y_pos]

    return x_cord, y_cord


def print_transect(x_cord, y_cord):

    print("\n----------------RANDOM TRANSECT GENERATOR---------------------------\n")  # NOQA
    print(
        "\nTransect Coordinates:\n"
        "|----X----|----Y----|\n"
    )
    for i, x in enumerate(x_cord):
            print("|   {x}   |   {y}   |\n".format(x=x_cord[i], y=y_cord[i]))
    print("\n\nTransect Directions:\n")
    print(
        "Note: In the following directions, `North' means the area ",
        "to the left of the transect when standing\nat the ",
        "start of the transect.",
        " 'South' means the area to the right of the transect,\n"
        "when standing at the start of the transect.\n"
    )
    print("Step 1: Mark the transect at the following locations:")
    for x in x_cord:
        print("\tx = {x} meters".format(x=x))
    print("\n")
    for i, x in enumerate(x_cord):
        n = i + 2
        print("Step {n}:".format(n=n))
        print("\tGo to x={x} on the transect".format(x=x))
        if y_cord[i] > 0:
            print("\t Go {x} meters 'North'".format(x=y_cord[i]))
        else:
            print("\t Go {x} meters 'South'".format(x=abs(y_cord[i])))
        print("\tSample a 5m radius plot at this location.")
        print("\n")
    print("All done!")


def make_transect():

    x_pos = make_x_pos()
    y_pos = make_y_pos()
    y_pos.extend(make_y_pos())
    x_cord, y_cord = make_coordinates(x_pos, y_pos)
    print_transect(x_cord, y_cord)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
