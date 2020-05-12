---
title: python script lottery (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lottery'


Modules used in program: 
* `import random as megamillions`
* `import random as powerball`

## python lottery

Python example: lottery

```python
import random as powerball
powerball.seed(raw_input("insert seed number: \n"))
sorted(powerball.sample(xrange(1, 69), 5)) + powerball.sample(xrange(1, 26), 1)

import random as megamillions
megamillions.seed(raw_input("insert seed number: \n"))
sorted(megamillions.sample(xrange(1, 70), 5)) + megamillions.sample(xrange(1, 25), 1)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
