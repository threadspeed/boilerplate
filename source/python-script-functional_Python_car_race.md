---
title: python script functional Python car race (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'functional Python car race'

Functions in program: 
* `def race(state):`
* `def draw(state):`
* `def run_step_of_race(state):`
* `def output_car(car_position):`
* `def move_cars(car_positions):`
* `def draw():`
* `def run_step_of_race():`
* `def draw_car(car_position):`
* `def move_cars():`

## python functional Python car race

Python mysql example: functional Python car race

```python
### Imperative version of the car race game. ###

from random import random

time = 5
car_positions = [1, 1, 1]

while time:
    # decrease time
    time -= 1

    print((''))
    for i in range(len(car_positions)):
        # move car
        if random() > 0.3:
            car_positions[i] += 1

        # draw car
        print(('-' * car_positions[i]) )
        
       
### Declarative NON functional version ###

# This technique uses functions, but it uses them as sub-routines. They parcel up code. 
# The code is not functional in the sense of the guide rope (the absence of side effects : it doesn’t rely on 
# data outside the current function, and it doesn’t change data that exists outside the current function.)
# ***The functions in the code use state that was not passed as arguments***. They affect the code around them by 
# changing external variables, rather than by returning values. To check what a function really does, 
# the reader must read each line carefully. If they find an external variable, they must find its origin. 
# They must see what other functions change that variable.

from random import random

# functions definition

def move_cars():
    for i, _ in enumerate(car_positions):
        if random() > 0.3:
            car_positions[i] += 1

def draw_car(car_position):
    print(('-' * car_position))

def run_step_of_race():
    global time
    time -= 1
    move_cars()

def draw():
    print((''))
    for car_position in car_positions:
        draw_car(car_position)

# main function
        
time = 5
car_positions = [1, 1, 1]

while time:
    run_step_of_race()
    draw()


### Declarative AND functional version. ###

# The code is still split into functions, but the functions are functional. 
# There are three signs of this. 
# First, there are no longer any shared variables. time and car_positions get passed straight into race(). 
# Second, functions take parameters. 
# Third, no variables are instantiated inside functions. All data changes are done with return values. 
# race() recurses with the result of run_step_of_race(). Each time a step generates a new state, it is passed 
# immediately into the next step.

from random import random

def move_cars(car_positions):
    return map(lambda x: x + 1 if random() > 0.3 else x,
               car_positions)

def output_car(car_position):
    return ('-' * car_position)

# This function updates the state of the game by modifying the dictionary values that will be passed 
# recursively to the `race()` function. 
def run_step_of_race(state):
    return {'time': state['time'] - 1,
            'car_positions': list(move_cars(state['car_positions']))}

def draw(state):
    print((''))
    print(('\n'.join(map(output_car, state['car_positions']))))
    
# The while loop of the previous version can be turned into a recursive function where the arguments returned 
# are modified by the run_step_of_race function up to `if state["time"]:` evaluates to FALSE (when time is 0).
def race(state):
    draw(state)
    if state['time']:
        race(run_step_of_race(state))

race({'time': 5,
      'car_positions': [1, 1, 1]})


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
