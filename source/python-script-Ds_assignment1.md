---
title: python script Ds assignment1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds assignment1'

Functions in program: 
* `def run():`
* `def is_vaild(x, y, h, w):`
* `def move(x, y, d, h, w):`
* `def h2(x, y, h, w):`
* `def h1(x, y, h, w):`
* `def solve(maze):`

Modules used in program: 
* `import heapq`

## python Ds assignment1

Python mysql example: Ds assignment1

```python
import heapq

EMPTY, WALL = 0, 1
DIRECTIONS = 'UDLR'


def solve(maze):
    heuristic = h2
    outstr = ''
    height = len(maze)
    width = len(maze[0])
    endnode = (height-1, width-1)

    pq = []
    pq.append((heuristic(0, 0, height, width), (0, 0)))
    fringes = {(0, 0): [(0, 0)]}

    while pq:
        _, node = heapq.heappop(pq)
        outstr += '{0} {1}\n'.format(node[0], node[1])

        if node == endnode:
            outstr += ''.join(map(str, fringes[node]))
            print(outstr, '\n')
            return
        else:
            for d in DIRECTIONS:
                newnode = move(*node, d, height, width)
                if newnode and \
                        newnode not in fringes and \
                        maze[newnode[0]][newnode[1]] == EMPTY:
                    fringes[newnode] = fringes[node] + [newnode]
                    heapq.heappush(pq,
                                   (len(fringes[newnode]) + heuristic(*newnode, height, width),
                                    newnode)
                                   )


def h1(x, y, h, w):
    """ Manhattan Distance """
    return (h - x) + (w - y)

def h2(x, y, h, w):
    """ Straight Distance """
    return ((h - x)**2 + (w - y)**2)**0.5

def move(x, y, d, h, w):
    if d == 'U':
        x -= 1
    elif d == 'D':
        x += 1
    elif d == 'L':
        y -= 1
    elif d == 'R':
        y += 1

    if is_vaild(x, y, h, w):
        return x, y
    else:
        return None


def is_vaild(x, y, h, w):
    return 0 <= x < h and 0 <= y < w

def run():
    for _ in range(int(input())):
        input()
        height, width = map(int, input().split())
        maze = []
        for _ in range(height):
            maze.append(list(map(int, input().split(','))))
        solve(maze)


if __name__ == '__main__':
    run()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
