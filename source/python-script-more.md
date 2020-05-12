---
title: python script more (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'more'

Functions in program: 
* `def format_board(b):`
* `def make_move(board, slot, p):`
* `def get_player():`
* `def get_computer(comp, opp):`
* `def free_space(board, space):`
* `def full_board():`
* `def check_winner(b, l):`
* `def make_new():`
* `def copy(item):`

Modules used in program: 
* `import random`

## python more

Python example: more

```python
import random

board = {
    1: 0, 2: 0, 3: 0,
    4: 0, 5: 0, 6: 0,
    7: 0, 8: 0, 9: 0
    }
  

computer = 1
player = 2



def copy(item):
    new = {}
    for k, v in item.items():
        new[k] = v
    return new

def make_new():
    for k in board.keys():
        board[k] = 0

def check_winner(b, l):
    return ((b[1]==l and b[2]==l and b[3]==l) or
        (b[4]==l and b[5]==l and b[6]==l) or
        (b[7]==l and b[8]==l and b[9]==l) or
        (b[1]==l and b[4]==l and b[7]==l) or 
        (b[2]==l and b[5]==l and b[8]==l) or
        (b[3]==l and b[6]==l and b[9]==l) or
        (b[1]==l and b[5]==l and b[9]==l) or
        (b[3]==l and b[5]==l and b[7]==l))

def full_board():
    for i in range(1, 10):
        if board[i]==0:
            return False
    return True
             
def free_space(board, space):
    return (board[space]==0)
            
def get_computer(comp, opp):
    
    ran = random.randint(1, 1000)
    if ran > 980:
        while True:
            move = random.randint(1, 9)
            if free_space(board, move):
                return move
            
    #win first
    for i in range(1, 10):
        cop = copy(board)
        if free_space(cop, i):
            make_move(cop, i, comp)
            if check_winner(cop, comp):
                return i
            
    #check edges
    for i in range(1, 10):
        cop = copy(board)
        if free_space(cop, i):
            make_move(cop, i, opp)
            if check_winner(cop, opp):
                return i
  
    while True:
        move = random.choice([1, 3, 7, 9])
        if free_space(board, move):
            return move
        else:
            break
    
    if free_space(board, 5):
        return 5
        
    while True:
        move = random.choice([2, 6, 4, 8])
        if free_space(board, move):
            return move
        else:
            break
    
    while True:
        move = random.randint(1, 9)
        if free_space(board, move):
            return move
    

def get_player():
    pass

def make_move(board, slot, p):
    board[slot] = p

def format_board(b):
    k = {
        0: " ",
        1: "X",
        2: "O"
        }
    
    string = """
 %s | %s | %s
---+---+---
 %s | %s | %s
---+---+---
 %s | %s | %s
""" % (k[b[1]], k[b[2]], k[b[3]], k[b[4]], k[b[5]], k[b[6]], k[b[7]], k[b[8]], k[b[9]])
    return string
    
print(format_board(board))

comp1 = 0
comp2 = 0
draw = 0
moves = 0
highest = 0
lowest = 9



for i in range(100):
    start = random.randint(1, 2)
    while True:
        if full_board():
            draw += 1
            break
        if start == 1:
            #comp1
            move = get_computer(computer, player)
            make_move(board, move, computer)
            moves += 1
            if check_winner(board, computer):
                print("Comp1 (X) Won", moves)
                print(format_board(board))
                print("~~~~~~~~~~~~~~~~~~~")
                comp1 += 1
                break
            if full_board():
                draw += 1
                break
            #comp2
            move = get_computer(player, computer)
            make_move(board, move, player)
            moves += 1
            if check_winner(board, player):
                print("Comp2 (O) Won", moves)
                print(format_board(board))
                print("~~~~~~~~~~~~~~~~~~~")
                comp2 += 1
                break
        elif start == 2:
            #comp2
            move = get_computer(player, computer)
            make_move(board, move, player)
            moves += 1
            if check_winner(board, player):
                print("Comp2 (O) Won", moves)
                print(format_board(board))
                print("~~~~~~~~~~~~~~~~~~~")
                comp2 += 1
                break
            if full_board():
                draw += 1
                break
            #comp1
            move = get_computer(computer, player)
            make_move(board, move, computer)
            moves += 1
            if check_winner(board, computer):
                print("Comp1 (X) Won", moves)
                print(format_board(board))
                print("~~~~~~~~~~~~~~~~~~~")
                comp1 += 1
                break
    if moves > highest:
        highest = moves
    if moves < lowest:
        lowest = moves
        print("!!!~~~~~~~~~~~~~~~~~~~!!!")
        print(format_board(board))
        print("!!!~~~~~~~~~~~~~~~~~~~!!!")
    moves = 0
    make_new()
print("Comp1:", comp1)
print("Comp2:", comp2)
print("Draws:", draw)
print("Least amount of moves:", lowest)
print("Most amount of moves:", highest)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
