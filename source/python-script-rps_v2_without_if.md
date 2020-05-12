---
title: python script rps v2 without if (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rps v2 without if'

Functions in program: 
* `def play():`
* `def player_choose():`

Modules used in program: 
* `import random`

## python rps v2 without if

Python example: rps v2 without if

```python
import random

CHOICES = ["rock", "paper", "scissors"]

def player_choose():
    choice = ""
    while choice not in CHOICES:
        choice = input("What do you choose? Rock, paper or scissors? ").lower()
    return choice

def play():
    score = [0, 0, 0, "tie", "win", "lose"] # (ties, wins, losses)
    while True:
        pc_choice = random.choice(CHOICES)
        player_choice = player_choose()
        result = (CHOICES.index(player_choice) - CHOICES.index(pc_choice)) % 3 # Returns 0 for tie, 1 for win and 2 for loss
        score[result] += 1
        print(f"I chose {pc_choice}! You {score[result + 3]}!") # Get the right string from score by bumping the index by 3
        print(f"Score is now {score[1]} wins, {score[2]} losses and {score[0]} ties.")
        again = input("Play again(Y/N)? ").lower()
        if again == "n":
            break
        print("I'll assume that means yes.")

if __name__ == "__main__":
    play()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
