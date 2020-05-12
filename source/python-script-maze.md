---
title: python script maze (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'maze'

Functions in program: 
* `def main():`
* `def draw_maze(height, width, links):`
* `def draw_cell_row(height, width, links, row):`
* `def draw_wall_row(height, width, links, row):`

Modules used in program: 
* `import argparse`
* `import random`

## python maze

Python mysql example: maze

```python
"""maze.py

This script generates a maze by using the Disjoint Set data structure.
Entrance of the generated maze is at the top-left corner, while exit
at the bottom-right corner.

I was inspired by this disjoint_set_maze_generator.py example and
implemented the code from scratch.

https://gist.github.com/schedutron/0077053a842e5925f31594bb473a8554

Usage:
$ python3 maze.py <height> <width>

Example:
$ python3 maze.py 8 20
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
  | |   |   |     | |   |     |         |
+ + +-+ +-+ +-+ +-+ +-+ + +-+-+-+ +-+-+-+
| | | |         |           |     |   | |
+ + + + + +-+ +-+ +-+-+ +-+-+ +-+-+ +-+ +
|   | | | | |   |     | | |       | |   |
+-+ + + +-+ + + + +-+-+-+ + + +-+-+ + +-+
| | |   | |   |       |   | |   | | |   |
+ + +-+ + +-+-+ +-+-+ + +-+-+ +-+ + + + +
|           |     |   |     | |       | |
+ + +-+ +-+-+-+-+ +-+ + +-+ + +-+-+-+-+ +
| | | | |   |     |   | |               |
+ +-+ + +-+ +-+ +-+-+ + +-+-+ +-+-+ +-+ +
| |       |         |   |   | |   | | | |
+ +-+-+ + +-+ +-+-+-+ + +-+ + +-+ +-+ + +
|   |   | |       |   | |             |  
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
"""


import random
import argparse

from disjoint_set import DisjointSet


def draw_wall_row(height, width, links, row):
    assert row < height + 1
    horizontals = [' ' if ((row -1) * width + i, row * width + i) in links else '-'
                   for i in range(width)]
    output = '+'.join(horizontals)
    print('+' + output + '+')


def draw_cell_row(height, width, links, row):
    assert row < height
    verticals = [' ' if (row * width + i, row * width + i + 1) in links else '|'
                 for i in range(width - 1)]
    output = ' '.join(verticals)
    if row == 0:
        print('  ' + output + ' |')
    elif row == height - 1:
        print('| ' + output + '  ')
    else:
        print('| ' + output + ' |')


def draw_maze(height, width, links):
    for j in range(height):
        draw_wall_row(height, width, links, j)
        draw_cell_row(height, width, links, j)
    draw_wall_row(height, width, links, height)


def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('height', type=int)
    parser.add_argument('width', type=int)
    args = parser.parse_args()
    height, width = args.height, args.width

    # There are (height * width) cells in the maze.  We use a disjoint
    # set to keep track of which cells have been connected together.
    cells = DisjointSet(height * width)

    # create a list of all possible walls between the cells
    walls  = [(j * width + i, j * width + i + 1)
              for j in range(height)
                  for i in range(width - 1)]
    walls += [(j * width + i, (j + 1) * width + i)
              for j in range(height - 1)
                  for i in range(width)]

    # randomize order of the walls
    random.shuffle(walls)

    # union the cells by breaking down randomized walls until all cells
    # are joint together
    num_of_unions = 0
    links = []
    for wall in walls:
        if cells.find(wall[0]) != cells.find(wall[1]):
            links.append(wall)
            cells.union(wall[0], wall[1])
            num_of_unions += 1
        # there are (height * width) cells in total, so we are done
        # after doing union for (height * width - 1) of times
        if num_of_unions >= (height * width - 1):
            break

    # draw/print(the output)
    draw_maze(height, width, links)


if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
