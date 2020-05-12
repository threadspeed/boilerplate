---
title: python script Learn TicTackToe (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Learn TicTackToe'

Functions in program: 
* `def start_game():`
* `def eval_board():`
* `def block_mark(player):`
* `def print_board():`
* `def reset_board():`

Modules used in program: 
* `import random`

## python Learn TicTackToe

Python example: Learn TicTackToe

```python
import random

board = [
    ['O', 'X', '-'],
    ['-', 'X', '-'],
    ['-', 'X', 'X']
]

players = {0: ['You', 'X'], 1: ['Me','O']}
status = ('Win', 'Tied', 'N/A')
def reset_board():
    global board
    board = [
        ['-', '-', '-'],
        ['-', '-', '-'],
        ['-', '-', '-']
    ]

def print_board():
    global board
    for row in board:
        print("|", end="")
        for column in row:
            print(column, end="|")
        print("")

def block_mark(player):
    global board
    name = players[player][0]
    symb = players[player][1]
    print('{}, Please enter a empty location to block {} is your symbol]'.format(name, symb))
    r = int(input('Row :'))
    c = int(input('Col :'))
    if (r > 3 or r < 0) or (c > 3 or c < 0):
        print("Invalid Location !")
        block_mark(player)
    if board[r][c] != '-':
        print("Location already Marked !")
        block_mark(player)
    board[r][c] = symb

def eval_board():
    global board
    a = set()
    for i in range(3):
        a = set(board[i])
        if len(a) == 1 and '-' not in a:
            return status[0]
        a = set([x[i] for x in board])
        if len(a) == 1 and '-' not in a:
            return status[0]
    a.clear()

    for i in range(3):
        a.add(board[i][i])
    if len(a) == 1 and '-' not in a:
        return status[0]

    j = 2
    a.clear()
    for i in range(3):
        a.add(board[i][j])
        j -= 1

    if len(a) == 1 and '-' not in a:
        return status[0]

    is_empty = False
    for i in range(3):
        if '-' in board[i]:
            is_empty = True
    if not is_empty:
        return status[1]

    return status[2]

def start_game():
    player = input('Enter name of Player 1 : ')
    players[0][0] = player
    player = input('Enter name of Player 2 : ')
    players[1][0] = player

    start_player = random.randrange(0, 2)
    current_player = start_player

    print("{name} Will Start the Game !".format(name=players[current_player][0]))
    reset_board()

    st = status[2]
    while True:
        block_mark(current_player)
        print_board()
        st = eval_board()
        if st == status[0]:
            print("Congratulations {} ! You Win This Round !".format(players[current_player][0]))
            break
        elif st == status[1]:
            print("This Board is Drawn, Restart the Game !")
            break
        else:
            current_player = (current_player + 1) % 2

start_game()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
