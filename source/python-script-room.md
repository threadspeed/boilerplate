---
title: python script room (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'room'


Modules used in program: 
* `import random`

## python room

Python example: room

```python
import random

class Room:

	def __init__(self, west, north, east, south, thingsInRoom):
		self.thingsInRoom = thingsInRoom
		self.west = west
		self.north = north
		self.east = east
		self.south = south

	def getWest(self):
		return self.west

	def getNorth(self):
		return self.north

	def getEast(self):
		return self.east

	def getSouth(self):
		return self.south

	def getRandRoom(self):
		choice = random.randint(0,3)
		print(choice)
		roomChoice = { 0: self.getWest(), 1: self.getNorth(), 2: self.getEast(), 3: self.getSouth() }
		return roomChoice[choice]

	def printContents(self):
		print(self.thingsInRoom)




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
