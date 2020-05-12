---
title: python script Demo 11 Objects (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Demo 11 Objects'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Demo 11 Objects

Python mysql example: Demo 11 Objects

```python
import random
import sys
import os

class Animal:
    __name = ""
    __height = 0
    __weight = 0
    __sound = 0

    def __init__(self, name, height, weight, sound):
        self.__name = name
        self.__height = height
        self.__weight = weight
        self.__sound = sound

    #Name
    def set_name(self, name):
        self.__name = name

    def get_name(self):
        return self.__name

    #Height
    def set_height(self, height):
        self.__height = height

    def get_height(self):
        return self.__height

    #Weight
    def set_weight(self, weight):
        self.__weight = weight

    def get_weight(self):
        return self.__weight

    #Sound
    def set_sound(self, sound):
        self.__sound = sound

    def get_sound(self):
        return self.__sound

    def  get_type(self):
        print("Animal")

    def toString(self):
        return "{} is {} cm tall and {} kilograms and says {}".format(self.__name,
                                                                      self.__height,
                                                                      self.__weight,
                                                                      self.__sound)

cat = Animal('Whiskers', 33, 10, 'Meow')

print(cat.toString())

class Dog(Animal):
    __owner = ""

    def __init__(self, name, height, weight, sound, owner):
        self.__owner = owner
        super(Dog, self).__init__(name, height, weight, sound)

    def set_owner(self, owner):
        self.__owner = owner

    def get_owner(self):
        return self.__owner

    def get_type(self):
        print("Dog")

    def toString(self):
        return "{} is {} cm tall and {} kilograms and says {} His owner is {}".format(self.__name,
                                                                      self.__height,
                                                                      self.__weight,
                                                                      self.__sound,
                                                                      self.__owner)


    def multiple_sounds(self, how_many = None):
        if how_many is None:
            print(self.get_sound())
        else:
            print(self.get_sound() * how_many)

spot = Dog("Spot", 53, 27, "Ruff", "Roy")

print(spot.toString())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
