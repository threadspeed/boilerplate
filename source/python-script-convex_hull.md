---
title: python script convex hull (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'convex hull'

Functions in program: 
* `def randPointsGen(size):`
* `def convexHull(points):`
* `def orientation(p, q, r):`

Modules used in program: 
* `import time`
* `import math`
* `import random                                                                                                                                                                [43/364]`

## python convex hull

Python example: convex hull

```python
import random                                                                                                                                                                [43/364]
import math
import time

def orientation(p, q, r):
    val = (q["y"] - p["y"]) * (r["x"] - q["x"]) -\
          (q["x"] - p["x"]) * (r["y"] - q["y"])
    if val == 0:
        return 0
    return  1 if (val > 0) else 2

def convexHull(points):
    n = len(points)
    if n < 3:
        return

    hull = []

    l = 0
    for i in range(n-1):
        if points[i+1]["x"] < points[l]["x"]:
            l = i+1
    p = l

    while True:
        hull.append(points[p])
        q = (p+1)%n
        for i in range(n):
            if orientation(points[p], points[i], points[q]) == 2:
                q = i
        p = q
        if p == l:
            break
        if len(hull) > len(points):
            print("Error!!")
            break

def randPointsGen(size):
    points = []
    root = math.sqrt(size/100)
    fixed_size = int(size/root)
    for i in range(size):
        point = {"x":random.randint(1, fixed_size), "y":random.randint(1, fixed_size)}
        while point in points:
            point = {"x":random.randint(1, fixed_size), "y":random.randint(1, fixed_size)}
                return points

if __name__ == "__main__":
    random.seed(time.time())
    f1 = open("result_convex_hull_100_1.csv", "w")
    f2 = open("result_convex_hull_1000_1.csv", "w")
    f3 = open("result_convex_hull_10000_1.csv", "w")

    for idx in range(1000):
        points = randPointsGen(100)
        start = time.time()*1000
        convexHull(points)
        end = time.time()*1000
        timeStamp = str(-start + end)
        if idx != 999:
            timeStamp += ","
        f1.write(timeStamp)

        points = randPointsGen(1000)
        start = time.time()*1000
        convexHull(points)
        end = time.time()*1000
        timeStamp = str(-start + end)
        if idx != 999:
            timeStamp += ","
        f2.write(timeStamp)

        points = randPointsGen(10000)
        start = time.time()*1000
        convexHull(points)
        end = time.time()*1000
        timeStamp = str(-start + end)
        if idx != 999:
            timeStamp += ","
        f3.write(timeStamp)
    f1.close()
    f2.close()
    f3.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
