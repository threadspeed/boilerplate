---
title: python script BicycleIndustry (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'BicycleIndustry'


Modules used in program: 
* `import random`

## python BicycleIndustry

Python mysql example: BicycleIndustry

```python
import random

class Bicycle(object):
    def __init__(self, bikeName, weight, prodCost):
        self.name = bikeName
        self.weight = weight
        self.cost = prodCost
        
class BikeShop(object):
    def __init__(self, shopName, stock):
        self.name = shopName
        self.stock = stock
        self.profit = 0
    
    def sell(self, Customer, Bicycle):
        if self.stock[Bicycle] > 0:
            Customer.owned.append(Bicycle)
            self.stock[Bicycle] -= 1
            Customer.fund -= Bicycle.cost
            self.profit += (Bicycle.cost * .2)
            
        else:
            print("Out of stock.")
    
class Customer(object):
    def __init__(self, custName, fund):
        self.name = custName
        self.fund = fund
        self.owned = []

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
