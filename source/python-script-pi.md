---
title: python script pi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pi'


Modules used in program: 
* `import math`
* `import random`

## python pi

Python mysql example: pi

```python
import random
import math

count_total = 10000
count_inside = 0

for _ in xrange(count_total):
    inside_the_unit_circle =  (math.hypot(random.random(), random.random()) < 1)
    count_inside += 1 if (inside_the_unit_circle) else 0

print(4.0 * count_inside / count)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
