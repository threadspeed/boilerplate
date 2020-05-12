---
title: python script pycharm test practice5 practice54 practice541 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice5 practice54 practice541'

Functions in program: 
* `def start_game():`
* `def start_game():`
* `def game_rules(total):`
* `def points_gen(num=3, points=None):`

Modules used in program: 
* `import random`

## python pycharm test practice5 practice54 practice541

Python example: pycharm test practice5 practice54 practice541

```python
#coding =  utf-8
#generate points
import random
def points_gen(num=3, points=None):
    print('Roll The Dice~')
    if points == None:
        points = []
    while num > 0:
        point = random.randrange(1,7)
        points.append(point)
        num = num - 1
    return points

#define rules of this game
def game_rules(total):
    isBig = 11 <= total <=18
    isSmall = 3 <= total <=10
    if isBig:
        return 'big'
    elif isSmall:
        return 'small'
'''
#game boday
def start_game():
    print('<<< GAME STARTS: >>>')
    real_point = points_gen()
    total = sum(real_point)
    b_s = game_rules(total)
    your_input = input('please input *big* or *small*: ')
    #该步用来验证输入是否合理的
    check = ['big','small']
    if your_input in check:
        if your_input == b_s:
            print('The points are:',real_point,'You WIN!!')
        else:
            print('The points are: ',real_point,'You LOSE!!')
    else:
        print('Invalid input, please check your input!')
        start_game()
'''
def start_game():
    your_money = 1000
    if your_money > 0:
        print('<<<<  Game Starts  >>>>')
        choise = ['big','small']
        your_choise = input('big or small: ')

        if your_choise in choise:
            your_bet = int(input('How much you wanna bet ? =='))
            points = points_gen()
            total = sum(points)
            youWin = your_choise == game_rules(total)
            if youWin:
                print('The poins are:  ', points,'You WIN!')
                print('You get {}, you have {} now!'.format(your_bet,your_money + your_bet))
                your_money = your_money + your_bet
            else:
                print('The points are:  ', points, 'You LOSE!')
                print('You lost {}, you have {} now!'.format(your_bet, your_money - your_bet))
                your_money = your_money - your_bet
        else:
            print('Invalid Input, Please check again!')
    else:
        print('Game Over!')

#调用游戏函数
start_game()









```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
