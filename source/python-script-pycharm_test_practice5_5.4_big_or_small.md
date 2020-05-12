---
title: python script pycharm test practice5 5.4 big or small (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice5 5.4 big or small'

Functions in program: 
* `def start_game():`
* `def roll_result(total):`
* `def roll_dice(numbers=3, points=None):`

Modules used in program: 
* `import random`
* `import random`

## python pycharm test practice5 5.4 big or small

Python mysql example: pycharm test practice5 5.4 big or small

```python
#coding=utf-8
'''
import random
point1 = random.randrange(1,7)
point2 = random.randrange(1,7)
point3 = random.randrange(1,7)
num_list = [point1 , point2 , point3]
sub_num = sum(num_list)
if 3 <= sub_num <=10:
    tmp_para = 'Small'
else:
    tmp_para = 'Big'
print('<<<< GAME STARTS! >>>>')
val_input = input('Big or Small: ')
print('<<<< ROLE THE DICE! >>>>')
print('The Points are: [{}], and the sum is: {}' .format(num_list,sub_num))
if val_input == tmp_para:
    print('Good Job! You WIN!!')
else:
    print('Sorry, You LOOSE!!')
'''

###################  参考： ###################
#定义生成点数的函数
import random
def roll_dice(numbers=3, points=None):
    print('<<< Roll The Dice! >>>')
    if points is None:
        points = []
    while numbers > 0:
        point = random.randrange(1,7)
        points.append(point)
        numbers = numbers - 1
    return points
'''
#验证函数用的
points = roll_dice()
print(points)
'''

#定义游戏规则
def roll_result(total):
    isBig = 11 <= total <= 18
    isSmall = 3 <= total <= 10
    if isBig:
        return 'big'
    elif isSmall:
        return 'small'
"""
"""
#游戏开始
def start_game():
    print('<<< Game Start >>>')
    choises = ['big','small']
    your_choise = input('big or small:')
    if your_choise in choises:
        points = roll_dice()
        total = sum(points)
        youWin = your_choise == roll_result(total)
        if youWin:
#           print('The points are: {}'.format(points) + ', You WIN!!')
            print('The points are:',points,'You WIN!')
        else:
            #print('The points are: {}'.format(points) + ', You LOOSE!!')
            print('The points are:', points, 'You LOSE!')
    else:
        print('Invalid Words!')
        start_game()
#开始调用函数
start_game()

#

#小结
'''
示例虽然长，但通过定义函数的方式实现，逻辑性、可扩展性较强，而且是“模块化”定制，松耦合。
要好好学习的！
'''


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
