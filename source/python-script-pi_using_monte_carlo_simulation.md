---
title: python script pi using monte carlo simulation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pi using monte carlo simulation'


Modules used in program: 
* `import random`
* `import random`

## python pi using monte carlo simulation

Python example: pi using monte carlo simulation

```python
import random
square_arm = 10000
radius = 50000
points_in_circle = []
import random
no_of_simulation = 1000000
counter = 0
random.seed(5000)
x_series = []
while (counter < no_of_simulation):
	x_series.append(random.uniform(-radius,radius))
	counter = counter + 1

counter = 0
y_series = []
random.seed(0)
while (counter < no_of_simulation):
	y_series.append(random.uniform(-radius,radius))
	counter = counter + 1
radius_square = radius * radius
counter = 0
while (counter < no_of_simulation):
	x = x_series[counter]
	y = y_series[counter]
	if ((x*x + y*y) < radius_square):
		points_in_circle.append((x, y))
	counter = counter + 1

print(len(points_in_circle))
from math import pi
print("Real pi/4 is " + str(pi/4))
print("Calculated pi/4 is " + str(float((len(points_in_circle))) / no_of_simulation))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
