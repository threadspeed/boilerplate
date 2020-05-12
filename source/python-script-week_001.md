---
title: python script week 001 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 001'


Modules used in program: 
* `import numpy as np`

## python week 001

Python example: week 001

```python
# Easy 1.1

rope = 48
part = 0.75

what_left_of_rope = rope * (1 - part)
print(what_left_of_rope, "метров")

# Easy 1.2

total = 900
adult_cost = 200
number_of_children = 2
number_of_adults = 3

child_cost = (total - number_of_adults * adult_cost) / number_of_children
print(child_cost, "рублей")

# Easy 1.3

km_per_day = 45
days = 10
days_back = 9

distance = km_per_day * days 
km_per_day_back = distance / days_back

print(km_per_day_back, "километров в день")

# Easy 1.4

dad = 42
diff_btw_dad_grandpa = 29
ratio_btw_dad_son = 3

grandpa = dad + diff_btw_dad_grandpa
son = round(dad / ratio_btw_dad_son)

print("Grandpa is %s years old. Son is %s years old." % (grandpa, son))

# Easy 2

name = input("Please enter a name.")
gender = input("Boy or girl?")
print("%s is a good %s!" % (name, gender.lower()))


# Hard 1

'''
we need to know how much she talks during each month

there are two possibilities:
1. text data (e.g. from her VK chats) for each month 
    (12 str variables, or a list of length 12 where each element is a str)

2. or already aggregated data:
    for each month we need some value that reflects how much she talked during that month
        (12 float or int variables, or a list of length 12 where each element is float or int)
'''

# Hard 2

''' 2 str variables: "день" and "ночь"
and 2 int variables for length of them
'''

day = "день"
night = "ночь"

daylenght = len(day)
nightlength = len(night)

print("День заканчивается на %s, ночь заканчивается на %s." % (day[daylenght - 1], night[nightlength - 1]))

# Hard 3

'''
We need int/float variables that represent time that Anya requires to get to school and back by different means of transportation
'''

mins_in_hour = 60

walk_and_bus_in_hrs = 1.5 # bus + walk (in hours)
walk_and_bus = walk_and_bus_in_hrs * mins_in_hour # bus + walk (in minutes)
bus_and_bus = 30 # bus + bus (in minutes)

# everything is in munites from now on

bus = bus_and_bus / 2 # bus in one direction 
walk = walk_and_bus - bus # walk in one direction
walk_and_walk = walk * 2 # walk to and from school

walk_and_walk_in_hrs = walk_and_walk / 60 # transform back into hours
print("%s hours" % walk_and_walk_in_hrs)

# Hard 4

'''
We need int variables that store info about:

- the total number of heads
- the total number of legs
- the number of legs that pigs have
- the number of legs that gooses have

- the number of pigs
- the number of gooses
'''

heads = 30
legs = 84

# 1 goose = 1 head + 2 legs
# 1 pig = 1 head + 4 legs

goose_legs = 2
pig_legs = 4

'''

possibility 1: solve a set of linear equations by yourself and then just let the python do the computations for you

# gooses + pigs = heads => gooses = heads - pigs
# gooses * goose_legs + pigs * pig_legs = legs
# (heads - pigs) * goose_legs + pigs * pig_legs = legs
# heads * goose_legs + pigs * (pig_legs - goose_legs) = legs

pigs = (legs - heads * goose_legs) / (pig_legs - goose_legs)
pigs = round(pigs)
gooses = heads - pigs
print("There are %s pigs and %s gooses." % (pigs, gooses))

'''

'''

possibility 2: make python solve a set of linear equations for you

# ax = b
# x = (gooses, pigs)

# gooses + pigs = heads
# => line 1 of a is (1, 1)

# gooses * goose_legs + pigs * pig_legs = legs
# => line 2 of a is (goose_legs, pig_legs))

# b is (heads, legs)

'''

import numpy as np

a = np.array([[1, 1], [goose_legs, pig_legs]])
b = np.array([heads, legs])
x = np.linalg.solve(a, b)

print("There are %s gooses and %s pigs." % (int(x[0]), int(x[1])))

# Hard 5

'''
Ice := cost of an ice cream
P := Petya's money
M := Masha's money

P + 7 = Ice
M + 1 = Ice
P + M < Ice

=> P < 1, M < 7
=> Ice < 8

P + 7 = Ice => Ice >= 7

=> Ice = 7
'''

diff_petya_ice = input("Сколько не хватает Пете для того, чтобы купить мороженое?") # how much money does Petya need in order to buy an ice-cream
diff_petya_ice = int(diff_petya_ice)
diff_masha_ice = input("Сколько не хватает Маше для того, чтобы купить мороженое?") # how much money does Mashs need in order to buy an ice-cream
diff_masha_ice = int(diff_masha_ice)

ice_is_less_than = diff_petya_ice + diff_masha_ice
ice_is_more_than = max(diff_petya_ice, diff_masha_ice)

ice_possible_cost = list(range(ice_is_more_than, ice_is_less_than))
if len(ice_possible_cost) == 1:
    print("Мороженое стоит",*ice_possible_cost, "рублей")
else:
    print("Возможная стоимость мороженого (в рублях):")
    print(*ice_possible_cost, sep =", ")

# Hard 3

'''Ask user for a number. Check whether it's odd or even.'''

number = input("Welcome to an odd/even calculator. What number would you like to check?")
try:
    number = int(number)
    if number % 2 == 0:
        print("%s is even" % number)
    else:
        print("%s is odd" % number)
except ValueError:
    print("I accept only integers. Sorry.")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
