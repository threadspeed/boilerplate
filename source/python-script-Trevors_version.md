---
title: python script Trevors version (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Trevors version'

Functions in program: 
* `def player_vote(the_player, hats):`
* `def play_game():`
* `def init_game():`

Modules used in program: 
* `import pdb`
* `import random`

## python Trevors version

Python example: Trevors version

```python
import random
import pdb

MAX_PLAYERS = 10
NUM_GAMES = 4000000
players = MAX_PLAYERS

def init_game():
    hats = []
    for player in range(MAX_PLAYERS):
        if random.randint(0,1):
            hats.append( 1 )# Red is 1
        else:
            hats.append( 0 ) # Blue is 0
    return hats


def play_game():
    hats = init_game()
    #hats = [0,1,1,1]
    correct_votes = 0
    incorrect_votes = 0
    vote = player_vote(0, hats)
    if hats[0] == vote:
        correct_votes += 1
    else:
        incorrect_votes += 1

    if correct_votes and not incorrect_votes:
        return (1,0)
    if incorrect_votes:
        return (0,1)
    return (0,0)



# VOTEING Strategy

def player_vote(the_player, hats):
    all_same = True
    red_hats = 0
    blue_hats = 0
    for other_player in range(players):
        if other_player == the_player:
            continue # Skip me
        else:
            if hats[other_player] == 0:
                blue_hats += 1
            else:
                red_hats += 1
    if blue_hats > red_hats:
        return 1 #vote red
    elif blue_hats < red_hats:
        return 0 #vote blue
    else:
        return 2 #defualt

if __name__ == "__main__":
    correct, incorrect = 0,0
    for i in range(NUM_GAMES):
        c,i = play_game()
        if c:
            correct += 1
        if i:
            incorrect += 1
        if i and c:
            raise Exception
    print("TOTAL: Correct: %s Incorrect: %s" % (correct, incorrect))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
