---
title: python script point (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'point'

Functions in program: 
* `def check_significant(lower, upper, observed):`
* `def compute_critical(perms):`
* `def permutations(p=99, n=100, marks=None):`
* `def average_nearest_neighbor_distance(points, mark = None):`
* `def euclidean_distance(a, b):`
* `def create_random_marked_points(n, marks = None):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import random`
* `import math`
* `import analytics`

## python point

Python example: point

```python
import analytics

import math
import random
import random
import numpy as np


class Point:

    def __init__(self, x = 0, y = 0, mark = []):
        self.x = x
        self.y = y
        self.mark = mark

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __radd__(self, other):
        return Point(self.x + other, self.y + other)

    def check_coincident(self, b):

        if b.x == self.x and b.y == self.y:
            return True

    def shift_point(self, x_shift, y_shift):

        self.x += x_shift
        self.y += y_shift

class PointPattern:
    
    def __init__(self):
        self.points = []
        self.marks = ['ying', 'yang', 'black', 'white']
        self.length = len(self.points)

    def add_point(self, point):
        self.points.append(point)

    def remove_point(self, index):
        del(self.points[index])

    def average_nearest_neighor(self, mark=None):
        return analytics.average_nearest_neighbor_distance(self.points, 
                mark)

    def count_coincident(self):
        counted = []
        count = 0
        for index, point in enumerate(self.points):
            for index2, point2 in enumerate(self.points):
                if index != index2 and point2 not in counted:
                    if point == point2:
                        counted.append(point2)
                        count += 1
        return count

    def list_marks(self):
        marks = []
        for point in self.points:
            while point.mark not in marks:
                marks.append(point.mark)
        return marks
                
    def points_by_mark(self, mark):

        points_to_return = []
        for point in self.points:
            if point.mark == mark:
                points_to_return.append(point)
        return points_to_return

    def generate_random_points(self, n = self.length, marks = None):

        point_list = analytics.create_random_marked_points(n, marks)
        return point_list

    def generate_realizations(p = 99, marks = None):
        neighbor_perms = []
        for i in range(p):
            neighbor_perms.append(
                    average_nearest_neighbor(
                        generate_random_points()))
        return neighbor_perms
           
    def get_critical(neighbor_perms):
        return max(perms), min(perms)

    def comupte_g(self, nsteps):
        ds = np.linspace(0, 1, nsteps)
        dist_counts = []
        for d in range(ds):
            min_dist = None
            for index, n in enumerate(nsteps):
                if index is not d:
                    if min_dist is None or min_dist > ds[d]:
                        min_dist = ds[d]
            dist_counts.append(min_dist)
        return sum(dist_counts)/nsteps

def create_random_marked_points(n, marks = None):
    point_list = []
    rand = random.Random()
    for i in range(n):
        rand_x = round(rand.uniform(0,1),2)
        rand_y = round(rand.uniform(0,1),2)
        if marks is None:
            point_list.append(Point(rand_x, rand_y))
        else:
            rand_mark = random.choice(marks)
            point_list.append(Point(rand_x, rand_y, rand_mark))
    return point_list
def euclidean_distance(a, b):

    distance = math.sqrt((a.x - b.x)**2 + (a.y - b.y)**2)
    return distance


def average_nearest_neighbor_distance(points, mark = None):

    new_points = []
    if mark is None:
        new_points = points
    else:
        for point in points:
            if point.mark is mark:
                new_points.append(point)

    dists = []
    for num1, point in enumerate(new_points):
        dists.append(None) 
        for num2, point2 in enumerate(new_points):
            if num1 is not num2:
                new_dist = euclidean_distance(point, point2)
                if dists[num1] == None:
                    dists[num1] = new_dist
                elif dists[num1] > new_dist:
                    dists[num1] = new_dist

    return sum(dists)/len(points)

def permutations(p=99, n=100, marks=None):

    neighbor_perms = []
    for i in range(p):
        neighbor_perms.append(average_nearest_neighbor_distance(create_random_marked_points(n),
            marks))
    return neighbor_perms

def compute_critical(perms):
    return max(perms), min(perms)

def check_significant(lower, upper, observed):
    return(lower <= observed or observed <= upper)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
