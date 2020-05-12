---
title: python script bicycle industry (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bicycle industry'


## python bicycle industry

Python example: bicycle industry

```python
# Bicycles should have model name, weight, and cost to produce
class Bike(object):
    
    def __init__(self, model, weight, cost):
        self.model = model
        self.weight = weight
        self.cost = cost
        
    def __repr__(self):
        return self.model
        
# Bike Shops should have a name and an inventory of different bicycles; shop charges 20% markup
class Bike_shop(object):
    
    def __init__(self, shop_name, margin):
        self.shop_name = shop_name
        self.profit = 0
        self.margin = margin
        self.inventory = {}
        self.sold = []
       
    def add_bikes(self, bike, count):
        self.inventory[bike] = count 
        return self.inventory
         
    def compute_price(self, bike):
        price = bike.cost * (1 + self.margin)
        return price
        
    def sell_bike(self, customer):
        
        # if bike in customer.affordable(self) and bike in self.inventory:
        import random
        bike = random.choice(customer.affordable(self))
        self.inventory[bike] -= 1
        self.sold.append(bike)
        customer.purchases.append(bike)
        # del self.inventory[bike]
        customer.budget -= self.compute_price(bike)
        self.profit += (self.compute_price(bike) - bike.cost)
    # elsewe
    #     print("Sorry you cant afford the bike")
    
    def print_stock(self):
        print("Current inventory for" + " " + str(self.shop_name) + ":")
        for bike in self.inventory:
            print(bike.model, self.inventory[bike])
            
    def __repr__(self):
        return self.shop_name
    
# Customers should have a name, fund of money to buy the bike, and can buy and own a bike
class Customer(object):
    
    def __init__(self, name, budget):
        self.name = name
        self.budget = budget
        self.affordable_bikes = []
        self.purchases = []
        
    def affordable(self, bikeshop):
        # {x:4, y:7, d:6}
        for bike in bikeshop.inventory:
            if self.budget >= bikeshop.compute_price(bike):
                self.affordable_bikes.append(bike)
        return self.affordable_bikes
            
    def __repr__(self):
        return self.name

    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
