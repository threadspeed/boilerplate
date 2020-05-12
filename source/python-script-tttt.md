---
title: python script tttt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tttt'

Functions in program: 
* `def next_move(my, grid):`
* `def maxmin(my, grid, strategy):`
* `def get_score(my, grid):`
* `def possible(grid):`
* `def print_grid(grid):`

Modules used in program: 
* `import random`

## python tttt

Python example: tttt

```python
import random

opmv = {'O': 'X', 'X': 'O'}

def print_grid(grid):
    print('\n' + '\n'.join(' '.join(line) for line in zip(*[iter(grid)]*3)))

def possible(grid):
    return [i for i in xrange(9) if grid[i] == '_']

def get_score(my, grid):
    ''' 1 if I win, -1 if I lose, 0 if unknown or tie '''
    for a, b, c in [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                    (0, 3, 6), (1, 4, 7), (2, 5, 8),
                    (0, 4, 8), (2, 4, 6)]:
        if grid[a] == grid[b] == grid[c] != '_':
            return (1 if grid[a] == my else -1)
    return 0

def maxmin(my, grid, strategy):
    ''' maxmin algorithm (can be improved by pruning '''
    best_score = get_score(my, grid)
    if best_score == 0:
        allpos = possible(grid)
        if allpos:
            best_score = (-1 if strategy == max else 1)
            for t in allpos:
                grid[t] = (my if strategy == max else opmv[my])
                score = maxmin(my, grid, (min if strategy == max else max))
                best_score = strategy(best_score, score)
                grid[t] = '_'
                if best_score == (1 if strategy == max else -1):
                    break
    return best_score

def next_move(my, grid):
    move_score = []
    for t in possible(grid):
        grid[t] = my
        move_score.append((t, maxmin(my, grid, min)))
        grid[t] = '_'
    print(move_score)
    for score in [1, 0, -1]:
        moves = [m[0] for m in move_score if m[1] == score]
        if moves:
            return random.choice(moves)

if __name__ == '__main__':
    while 1:
        grid = ['_'] * 9
        turn = 'X'
        while '_' in grid and get_score(turn, grid) == 0:  # game not over
            print_grid(grid)
            print('Turn for', turn + ':')
            t = next_move(turn, grid)
            print('My move', t / 3 + 1, t % 3 + 1)
            grid[t] = turn
            turn = opmv[turn]
        print_grid(grid)
        print('Finished!')
        print(('X win!', 'Tie!', 'O win!')[get_score('O', grid) + 1])
        raw_input()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
