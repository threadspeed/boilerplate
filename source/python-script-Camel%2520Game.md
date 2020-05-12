---
title: python script Camel%2520Game (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Camel%2520Game'


Modules used in program: 
* `import random`
* `import random`

## python Camel%2520Game

Python example: Camel%2520Game

```python
#Camel Game
done=True
import random
water=100
thirst=0
n_movement=0
c_tiredness=0
miles=0
miles2=0
import random
print("welcome to the Camel Game")
print("You have stolen a camel to make your way across the Mobi desert. The natives want their camel back and are chasing you down! Survive your desert trek and outrun the natives")
while done:
    print("A ""Drink from your canteen")
    print("B " "Ahead moderate speed")
    print("C " "Ahead full speed")
    print("D " "Stop and Rest")
    print("E " "Status Check")
    print("Q " "Quit")
    answer=input("What will you do ")
    if answer=="Q":
        exit()
    elif answer=="A":
        print("you drank from your canteen")
        water=water-20
        thirst=0
        n_movement=random.randrange(1,4)
    elif answer=="B":
        miles=miles+random.randrange(10,15)
        thirst=thirst+1
        n_movement=n_movement+random.randrange(1,4)
        c_tiredness=c_tiredness+1
        print("you moved",miles,"miles")
    elif answer=="C":
        miles2=random.randrange(10,30)
        n_movement=n_movement+random.randrange(1,4)
        thirst=thirst+2
        c_tiredness=c_tiredness+2
        print("you moved",miles2,"miles")
    elif answer=="D":
        print("you stopped to rest")
        n_movement=n_movement+random.randrange(1,4)
        c_tiredness=0
        print("your camel is happy and",c_tiredness,"% tired")
    elif answer=="E":
        print("the natives are",miles+miles2-n_movement,"miles behind you")
        print("your thirst is at,",thirst)
        print("your camel is" ,c_tiredness,"% tired")
        print("you've traveled",miles+miles2, "miles")
        print("your water is at",water,"%")
    if n_movement > miles + miles2:
        print("you lost, the natives caught you")
        done=False
    if miles+miles2 > 100:
        print("you won")
        done=False
    if thirst > 8:
        print("you lost, you died of dehydration")
        done=False
    if c_tiredness > 8:
        print("you lost, your camel died")
        done=False

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
