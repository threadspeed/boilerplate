---
title: python script Ds duel (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds duel'

Functions in program: 
* `def series():`
* `def game(player):`
* `def cost(move):`

## python Ds duel

Python example: Ds duel

```python
from qplayer import Player as Player1
from player3 import Player as Player2

player = [Player1(), Player2()]

VERBOSE = True
move_to_string = {0:'0', 1:'1', 2:'2', -1:'-', -2:'='}
stringlist = []
movehistory = [[], []]

decision = \
{
    ( 0, 0): 0, ( 0, 1): 1, ( 0, 2): 1, ( 0,-1): 0, ( 0,-2): 0,
    ( 1, 0):-1, ( 1, 1): 0, ( 1, 2): 1, ( 1,-1): 0, ( 1,-2):-1,
    ( 2, 0):-1, ( 2, 1):-1, ( 2, 2): 0, ( 2,-1):-1, ( 2,-2): 0,
    (-1, 0): 0, (-1, 1): 0, (-1, 2): 1, (-1,-1): 0, (-1,-2): 0,
    (-2, 0): 0, (-2, 1): 1, (-2, 2): 0, (-2,-1): 0, (-2,-2): 0
}


def cost(move):
    if move > 0:
        return move
    elif move == 0:
        return -1
    else:
        return 0


def game(player):
    MAX_TURNS = 20
    alive = [True, True]
    energy = [0, 0]
    move = [p.new() for p in player]
    global stringlist, movehistory
    movehistory = [[move_to_string[m]] for m in move]

    def reward(self):
        other= 1-self
        if alive[self] and not alive[other]:
            return 1
        elif not alive[self] and alive[other]:
            return -1
        else:
            return 0

    for turn in range(MAX_TURNS):
        for self in range(2):
            if energy[self] < cost(move[self]):
                alive[self] = False
            else:
                energy[self] += -cost(move[self])

        if all(alive):
            tmove = tuple(move)
            if decision[tmove] != 0:
                if decision[tmove] == -1:
                    alive[1] = False
                if decision[tmove] == 1:
                    alive[0] = False

        prev = move[:]
        for self in range(2):
            other = 1-self
            move[self] = player[self].play(prev[other],
                                           energy[self],
                                           energy[other],
                                           reward(self))
            movehistory[self].append(move_to_string[move[self]])

        if not all(alive):
            return reward(0), reward(1)

    return 0,0


def series():
    MAX_GAMES = 10000
    scoreboard = [0, 0, 0]
    global stringlist

    for i in range(MAX_GAMES):
        stringlist.append('<GAME %d>' % i)
        g = game(player)
        scoreboard[g[0]] += 1

        stringlist.append(''.join(movehistory[0][:-1]))
        stringlist.append(''.join(movehistory[1][:-1]))

        if g[0] == 1:
            winstr = '%s win' % str(Player1.__module__)
        elif g[0] == 0:
            winstr = 'Draw'
        else:
            winstr = '%s win' % str(Player2.__module__)

        stringlist.append('Result: %s' % winstr)

    if VERBOSE: print('\n'.join(stringlist))

    print()
    print(Player1.__module__, scoreboard[1]+0.5*scoreboard[0])
    print(Player2.__module__, scoreboard[-1]+0.5*scoreboard[0])


if __name__=='__main__':
    series()
    print(*player[0].qtable, sep='\n')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
