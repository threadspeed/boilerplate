---
title: python script rock paper scissors (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rock paper scissors'


## python rock paper scissors

Python example: rock paper scissors

```python
answer = "yes"
while(answer != "no"):
    player1 = input("Rock/Paper/Scissors?")
    player2 = input("Rock/Paper/Scissors?")
    rock_scissors = player1 == "Rock" and player2 == "Scissors"
    scissors_rock = player2 == "Rock" and player1 == "Scissors"
    scissors_paper = player1 == "Scissors" and player2 == "Paper"
    paper_scissors = player2 == "Scissors" and player1 == "Paper"
    paper_rock = player1 == "Paper" and player2 == "Rock"
    rock_paper = player2 == "Paper" and player1 == "Rock"
    draw = player1 == player2
    if rock_scissors or scissors_paper or paper_rock:
        print("Player 1 wins")
    elif scissors_rock or paper_scissors or rock_paper:
        print("Player 2 wins")
    else:
        print("It's a draw")
    answer = input("New game (yes/no)?")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
