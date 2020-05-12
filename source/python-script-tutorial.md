---
title: python script tutorial (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tutorial'


Modules used in program: 
* `import CONSTANTS`
* `import random`

## python tutorial

Python example: tutorial

```python
import random
import CONSTANTS

class World:
    def __init__(self, world_name):
        self.name = world_name
        self.people = []
        self.buildings = []

    def add_person(self, person):
        self.people.append(person)
        return self.people

    def population(self):
        return len(self.people)

    def get_people(self):
        all_people = []
        for i in self.people:
            all_people.append(i.__dict__)
        return all_people
    
    def most_common_names(self):
        names = {"Alan": 0, "James": 0, "John":0, "Alice":0, "Christina":0 , "Elizabeth":0}
        for i in self.people:
            names[i.name] += 1
        return names
    
    #================================================#
    
class Person:
    def __init__(self, world, age, name=None, gender=None):
        if gender:
            self.gender = gender
        else:
            self.gender = Person.generate_gender()
        if name:
            self.name = name
        else:
            self.name = Person.generate_name(self.gender)
        
        self.age = age
        self.owned = []
        world.add_person(self)        
        
    @staticmethod
    def generate_gender():
        index = random.randrange(2)                    

        gender_selection = CONSTANTS.genders[index]
        
        return gender_selection
        

    @staticmethod
    def generate_name(gender=None):
        """
        returns gender based names 
        """
        if gender == "Male":
            names = CONSTANTS.male_names
        elif gender == "Female":
            names = CONSTANTS.female_names
        elif not gender:
            names = CONSTANST.male_names + CONSTANTS.female_names
        else:
            raise Exception("{} is not a valid gender".format(gender))

        return random.choice(names)

    def add_housing(self, housing):
        housing_info = {}
        print(dir(housing))
        # self.owned[housing.id] = 
        
    def get_age(self):
        return self.my_age

    def set_name(self, new_name):
        self.name = new_name
        return "Your new name is {}".format(self.name)

earth = World("Earth")

for i in range(1000):
    person = Person(earth, 20)

    

print("Earth has a population of {}".format(earth.population()))
print(earth.most_common_names())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
