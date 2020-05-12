---
title: python script Gambler's%2520Ruin%2520Simulator%2520from%2520Scratch%2520V0.2%2520 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Gambler's%2520Ruin%2520Simulator%2520from%2520Scratch%2520V0.2%2520'

Functions in program: 
* `def gambling():`
* `def setSimulatingCount():`
* `def setCapital():`
* `def setProbability():`

Modules used in program: 
* `import math`
* `import random`

## python Gambler's%2520Ruin%2520Simulator%2520from%2520Scratch%2520V0.2%2520

Python example: Gambler's%2520Ruin%2520Simulator%2520from%2520Scratch%2520V0.2%2520

```python
import random
import math

def setProbability():
    while(1):
        print('도박꾼이 한 세트에서 이길 확률은? ')
        P_gambler = float(input())
        
        if P_gambler < 0 or P_gambler > 1:
            print('0<=p<=1!! try again')
        else:
            P_casino = 1-P_gambler
            print('=> 카지노가 한 세트에서 이길 확률:', P_casino)
            break
            
    return P_gambler, P_casino

def setCapital():
    while(1):
        print('도박꾼의 초기 자본금은?')
        capital_of_gambler = int(input())
        
        if capital_of_gambler <= 0:
            print('You can\'t enter the casino if you don\'t have money')
        else:
            break
            
    while(1):    
        print('카지노의 초기 자본금은?')
        capital_of_casino = int(input())
        
        if capital_of_casino <= 0:
            print('You can\'t run the casino if you don\'t have money')
        else:
            break
            
    return capital_of_gambler, capital_of_casino

def setSimulatingCount():
    while(1):
        print('시행 횟수는?')
        simulating_count = int(input())
        
        if simulating_count <= 0:
            print('You have to play the game more than once')
        else:
            break
            
    return simulating_count

def gambling():
    
    simulating_count = setSimulatingCount()
    P_gambler, P_casino = setProbability()
    capital_of_gambler, capital_of_casino = setCapital()
    
    gambling_count = 0
    win_count_gambler = 0
    win_count_casino = 0
    
    roulette = list([0]*round(P_gambler*100)+[1]*round(P_casino*100))
    random.shuffle(roulette)
    
    # Roulette Checking.
    #print('겜블러가 승리:',roulette.count(0),'카지노가 승리:',roulette.count(1))
    #print(roulette)
    for _ in range(simulating_count):
        A, B = capital_of_gambler, capital_of_casino
        
        # Check Capital Initializing in Loop
        #print('겜블러 초기 자본:',A,'카지노 초기 자본:',B)
        while(A>0 and B>0): # Play the game until someone is bankrupt.
            if gambling_count > 1000000:
                print('countError: over million game')
                break
                
            spin_the_roulette = random.choice(roulette)    
            if spin_the_roulette == 0: # gambler wins the single game.
                A += 1
                B -= 1
                gambling_count += 1
                #print('gambler wins the set')
                #print('gambler:',A,'Casino:',B)
                
            elif spin_the_roulette == 1: # casino wins the single game.
                A -= 1
                B += 1
                gambling_count += 1
                #print('casino wins the set')
                #print('gambler:',A,'Casino:',B)
                
        #print(gambling_count,'번의 set 후 gambler의 잔고:', A)
        #print(gambling_count,'번의 set 후 casino의 잔고:', B)
        gambling_count = 0
            
        if A == 0:
            win_count_casino += 1
            #print('---------------------')
            #print('casino wins the game', win_count_casino)
        elif B == 0:
            win_count_gambler += 1
            #print('----------------------')
            #print('gambler wins the game', win_count_gambler)
            
    print('==========================================')
    print('도박꾼이 카지노를 파산시킬 확률은', (win_count_gambler/(win_count_gambler+win_count_casino)))

gambling()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
