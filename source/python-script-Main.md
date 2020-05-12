---
title: python script Main (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Main'

Functions in program: 
* `def statusCallback(status):`
* `def randArr(start, end, size):`

Modules used in program: 
* `import pprint`
* `import time`
* `import random as rand`
* `import numpy as np`

## python Main

Python example: Main

```python
import numpy as np
import random as rand
import time
import pprint

pp = pprint.PrettyPrinter(indent=4)

from ClusterPlotter import ClusterPlotter
from KMeans import KMeans


def randArr(start, end, size):
    """
    Generates an random Tuple[]
    :param start: random numbers starting at...
    :param end: random numbers ending at...
    :param size: how many Array items to generate
    :return: an Tuple[]
    """
    arr = []
    for i in range(size):
        arr.append([rand.randint(start, end), rand.randint(start, end)])
    return arr


def statusCallback(status):
    """
    Function as callback to every clustering, calls ClusterPlotter.cartesian() and waits for n seconds
    :param status: the Status callback parameter from KMeans
    """
    ClusterPlotter.cartesian(status["clusters"], status["centroids"])
    time.sleep(1)


# Additional random Data
coordinates = (randArr(0, 22, 100) + randArr(20, 80, 100))
coordinatesTransposed = np.transpose(coordinates)

# The K-Means clusterer
clusterer = KMeans(coordinates, 5)
clusterer.onCluster(statusCallback)

# Perform K-Means
clusterer.run()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
